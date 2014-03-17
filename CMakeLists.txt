cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

# Define project settings
project(Document)

FIND_PACKAGE(LATEX)

IF(PDFLATEX_COMPILER)

	set(Document_LANGUAGES fr en)
	foreach(lang ${Document_LANGUAGES})

		set(Document_OUTPUT_FILE_${lang} boucheny_cv-${lang}.pdf)
		set(Document_SOURCE_FILE_${lang} cv-${lang}.ltx)
		file(GLOB Document_CONTENT_FILES_${lang} *.ltx)

		ADD_CUSTOM_COMMAND(
			OUTPUT    ${Document_OUTPUT_FILE_${lang}}
			COMMAND   ${PDFLATEX_COMPILER}
			ARGS      ${Document_SOURCE_FILE_${lang}}
			DEPENDS   ${Document_CONTENT_FILES_${lang}}
			COMMENT   "Pdf2Ltx"
			)

		ADD_CUSTOM_TARGET(${lang} ALL echo ${lang}
			DEPENDS   ${Document_OUTPUT_FILE_${lang}}
			)

	endforeach()

ENDIF()
