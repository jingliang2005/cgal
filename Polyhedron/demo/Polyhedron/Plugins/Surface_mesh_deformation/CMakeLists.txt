include(polyhedron_demo_macros)

if(TARGET CGAL::Eigen3_support AND "${EIGEN3_VERSION}" VERSION_GREATER "3.1.90")

  polyhedron_demo_plugin(edit_plugin Edit_polyhedron_plugin Deform_mesh.ui)
  target_link_libraries(edit_plugin PUBLIC scene_surface_mesh_item
                                           scene_edit_item scene_selection_item)

  if(BUILD_TESTING AND NOT CMAKE_VS_MSBUILD_COMMAND)
    set_tests_properties(
      compilation_of__edit_plugin
      PROPERTIES RESOURCE_LOCK Selection_test_resources)
  endif()

else()
  message(STATUS "NOTICE: The polyhedron edit plugin requires Eigen 3.2 (or higher) and will not be available.")
endif()
