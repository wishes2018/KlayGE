SET(OPENALSDK_DIR "${EXTERNAL_PROJECT_DIR}/OpenALSDK")
SET(OPENAL_NAME "OpenAL32.dll")
SET(WRAP_OAL_NAME "wrap_oal.dll")
SET(REL_PATH "External/Downloads/OpenALSDK.7z")
SET(PACKAGE_FILE_ID "441882672e751bed1dcfc70f276b88aa7ac8040f")

DOWNLOAD_PACKAGE("OpenALSDK" ${REL_PATH} ${PACKAGE_FILE_ID})

SET(OPENAL_SRC_PATH "${OPENALSDK_DIR}/redist/${KLAYGE_PLATFORM_NAME}/${OPENAL_NAME}")
SET(WRAP_OAL_SRC_PATH "${OPENALSDK_DIR}/redist/${KLAYGE_PLATFORM_NAME}/${WRAP_OAL_NAME}")
SET(OPENAL_REDIST_PATH "${KLAYGE_BIN_DIR}/${OPENAL_NAME}")
SET(WRAP_OAL_REDIST_PATH "${KLAYGE_BIN_DIR}/${WRAP_OAL_NAME}")
ADD_CUSTOM_COMMAND(OUTPUT ${OPENAL_REDIST_PATH}
	COMMAND ${CMAKE_COMMAND} -E copy_if_different ${OPENAL_SRC_PATH} ${OPENAL_REDIST_PATH})
ADD_CUSTOM_COMMAND(OUTPUT ${WRAP_OAL_REDIST_PATH}
	COMMAND ${CMAKE_COMMAND} -E copy_if_different ${WRAP_OAL_SRC_PATH} ${WRAP_OAL_REDIST_PATH})
ADD_CUSTOM_TARGET(OpenALRedist ALL DEPENDS ${OPENAL_REDIST_PATH} ${WRAP_OAL_REDIST_PATH})

set_target_properties(OpenALRedist PROPERTIES FOLDER "${EXTERNAL_VS_FOLDER_PREFIX}/OpenALSDK")
