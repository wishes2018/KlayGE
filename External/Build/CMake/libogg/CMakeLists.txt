SET(LIBOGG_PROJECT_DIR "${EXTERNAL_PROJECT_DIR}/libogg")
SET(LIBOGG_OUTPUT_DIR "${EXTERNAL_PROJECT_DIR}/lib/libogg/${KLAYGE_PLATFORM_NAME}")

UpdateExternalLib("libogg" "libogg" "https://github.com/xiph/ogg.git" "0acd32d7cabf7e41cc29ea7c2bbffde969ff1ba0")

SET(BUILD_SHARED_LIBS OFF)
SET(BUILD_FRAMEWORK OFF)

ADD_SUBDIRECTORY(${LIBOGG_PROJECT_DIR} "${CMAKE_CURRENT_BINARY_DIR}/ogg")

SET_TARGET_PROPERTIES(ogg PROPERTIES
	ARCHIVE_OUTPUT_DIRECTORY ${LIBOGG_OUTPUT_DIR}
	ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${LIBOGG_OUTPUT_DIR}
	ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${LIBOGG_OUTPUT_DIR}
	ARCHIVE_OUTPUT_DIRECTORY_RELWITHDEBINFO ${LIBOGG_OUTPUT_DIR}
	ARCHIVE_OUTPUT_DIRECTORY_MINSIZEREL ${LIBOGG_OUTPUT_DIR}
	PROJECT_LABEL ogg
	DEBUG_POSTFIX ${CMAKE_DEBUG_POSTFIX}
	OUTPUT_NAME ogg_static${KLAYGE_OUTPUT_SUFFIX}
	FOLDER "${EXTERNAL_VS_FOLDER_PREFIX}/libogg"
)
