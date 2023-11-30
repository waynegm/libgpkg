# Usage

libgpkg is compiled as a [SQLite loadable extension](https://www.sqlite.org/loadext.html). To use the functionality provided by libgpkg
you will need to either load it using the [sqlite3_load_extension](https://www.sqlite.org/c3ref/load_extension.html) C function
provided by SQLite or via the [load_extension SQL function](https://www.sqlite.org/lang_corefunc.html#load_extension).

libgpkg provides does not provide an ```sqlite3_extension_init``` entry point. Instead it provides the following entry points; one of which should be specified when loading the extension:

    sqlite3_gpkg_init: the default entry point that is used automatically by recent versions of SQLite. When libgpkg is initialized using this entry point it will create GeoPackage compliant databases and support reading and writing of GPB encoded geometry blobs.
    sqlite3_gpkg_spl3_init: initializes libgpkg in Spatialite 3.x compatibility mode. libgpkg will reading and writing of Spatialite 3.x metadata tables and Spatialite geometry blobs.
    sqlite3_gpkg_spl4_init: initializes libgpkg in Spatialite 4.x compatibility mode. libgpkg will reading and writing of Spatialite 4.x metadata tables and Spatialite geometry blobs.
    sqlite3_gpkg_auto_init: attempts to autodetect the applicable mode based on the contents of the database. If the correct mode could not be determined GeoPackage mode will be used by default.

Once libgpkg has been loaded into SQLite a set of spatial SQL functions will become available via the SQL interface.

