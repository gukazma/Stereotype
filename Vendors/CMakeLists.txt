if(NOT TARGET colmap_sfm)
    option(GUI_ENABLED "Whether to enable the graphical UI" OFF)
    option(CUDA_ENABLED "Whether to enable CUDA, if available" OFF)
    add_subdirectory(colmap)
    set_target_properties(colmap_sources PROPERTIES FOLDER
        Vendors/colmap)
endif()
