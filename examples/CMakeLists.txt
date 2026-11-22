add_executable(graph_logist2 graph_logist2.cpp)
target_link_libraries(graph_logist2 mathplot_modules)

add_executable(jsonconfig jsonconfig.cpp)
target_link_libraries(jsonconfig mathplot_modules)

add_executable(triangle_intersect triangle_intersect.cpp)
target_link_libraries(triangle_intersect mathplot_modules)
 
add_executable(show_boundingboxes show_boundingboxes.cpp)
target_link_libraries(show_boundingboxes mathplot_modules)

add_executable(izhikevich izhikevich.cpp)
target_link_libraries(izhikevich mathplot_modules)

add_executable(izhikevich_alt izhikevich_alt.cpp)
target_link_libraries(izhikevich_alt mathplot_modules)

set(ANNEAL_ASA_MODULES
  ${MATHS_SOURCE_DIR}/sm/anneal.cppm
)
list(REMOVE_DUPLICATES ANNEAL_ASA_MODULES)

# Adaptive Simulated Annealing algo on a made up objective
add_executable(anneal_asa anneal_asa.cpp)
target_compile_definitions(anneal_asa PUBLIC VISUALISE)
target_sources(anneal_asa PUBLIC FILE_SET CXX_MODULES BASE_DIRS ${PROJECT_SOURCE_DIR}
  FILES ${ANNEAL_ASA_MODULES}
)
target_link_libraries(anneal_asa mathplot_modules)

add_executable(anneal_asa_novis anneal_asa.cpp)
set(ANNEAL_ASA_NOVIS_MODULES
  ${SM_CONFIG_MODULES}
  ${MPLOT_MATHS_CORE_MODULES}
  ${MPLOT_MATHS_HEXGRID_MODULES}
  ${MATHS_SOURCE_DIR}/sm/anneal.cppm
)
list(REMOVE_DUPLICATES ANNEAL_ASA_NOVIS_MODULES)
target_sources(anneal_asa_novis PUBLIC FILE_SET CXX_MODULES BASE_DIRS ${PROJECT_SOURCE_DIR}
  FILES ${ANNEAL_ASA_NOVIS_MODULES}
)
target_include_directories(anneal_asa_novis AFTER PRIVATE ${JSON_SOURCE_DIR}/include)

# Adaptive Simulated Annealing algo on objective from Bohachevsky
add_executable(anneal_boha anneal_asa.cpp)
target_compile_definitions(anneal_boha PUBLIC USE_BOHACHEVSKY_FUNCTION VISUALISE)
target_sources(anneal_boha PUBLIC FILE_SET CXX_MODULES BASE_DIRS ${PROJECT_SOURCE_DIR}
  FILES ${ANNEAL_ASA_MODULES}
)
target_link_libraries(anneal_boha mathplot_modules)
