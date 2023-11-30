# SQL Function Reference
# Conventions

SQL functions are listed in the form `<return type> <name>(<param 1 name> <param 1 type>, <param 2 name> <param 2 type>, ...). Parameter declarations enclosed in square brackets are optional parameters.
Table Creation Functions

InitSpatialMetadata([database_name text])

CheckSpatialMetadata([database_name text])

AddGeometryColumn([database_name text], table_name text, column_name text, geometry_type text, srid integer, [z integer, m integer])

CreateTilesTable([database_name text], table_name text)

CreateSpatialIndex([database_name text], table_name text, geometry_column text, primary_key_column text)

## Geometry IO Functions

blob ST_AsBinary(geometry blob), blob ST_GeomFromWKB(wkb blob), blob ST_WKBToSQL(wkt blob)

text ST_AsText(geometry blob), blob ST_GeomFromText(wkt text), blob ST_WKBFromText(wkt text), blob ST_WKTToSQL(wkt text)

## Geometry Creation Functions

blob ST_Point(x,y[,z,m] [,srid]), blob ST_MakePoint(x,y[,z,m] [,srid])

## Geometry Inspection Functions

double ST_MinX(geometry blob)
double ST_MaxX(geometry blob)
double ST_MinY(geometry blob)
double ST_MaxY(geometry blob)
double ST_MinZ(geometry blob)
double ST_MaxZ(geometry blob)
double ST_MinM(geometry blob)
double ST_MaxM(geometry blob)

int ST_SRID(geometry blob)

int ST_IsValid(geometry blob)

int ST_IsMeasured(geometry blob)

int ST_Is3d(geometry blob)

int ST_CoordDim(geometry blob)

int ST_GeometryType(geometry blob)

## Advanced Geometry Functions (requires GEOS)

double ST_Area(geometry blob)
double ST_Length(geometry blob)

int ST_IsSimple(geometry blob)
int ST_IsRing(geometry blob)
int ST_IsValid(geometry blob)

int ST_Disjoint(geometry1 blob, geometry2 blob)
int ST_Intersects(geometry1 blob, geometry2 blob)
int ST_Touches(geometry1 blob, geometry2 blob)
int ST_Crosses(geometry1 blob, geometry2 blob)
int ST_Within(geometry1 blob, geometry2 blob)
int ST_Contains(geometry1 blob, geometry2 blob)
int ST_Overlaps(geometry1 blob, geometry2 blob)
int ST_Equals(geometry1 blob, geometry2 blob)
int ST_Relate(geometry1 blob, geometry2 blob, intersectionMatrixPattern text)
int ST_Distance(geometry1 blob, geometry2 blob)
int ST_HausdorffDistance(geometry1 blob, geometry2 blob)

blob ST_Boundary(geometry blob)
blob ST_ConvexHull(geometry blob)
blob ST_Envelope(geometry blob)

blob ST_Difference(geometry1 blob, geometry2 blob)
blob ST_SymDifference(geometry1 blob, geometry2 blob)
blob ST_Intersection(geometry1 blob, geometry2 blob)
blob ST_Union(geometry1 blob, geometry2 blob)

blob ST_Buffer(geometry blob, distance double)

blob ST_Centroid(geometry blob)

int ST_NumPoints(geometry blob)
blob ST_PointN(geometry blob, n int)
blob ST_StartPoint(geometry blob)
blob ST_EndPoint(geometry blob)

int ST_NumInteriorRings(polygon blob)
blob ST_InteriorRingN(polygon blob, n int)
blob ST_ExteriorRing(polygon blob)

int ST_NumGeometries(geometry_collection blob)
blob ST_GeometryN(geometry_collection blob, n int)

## Available with GEOS 3.3+

int ST_IsClosed(geometry blob)
int ST_Covers(geometry1 blob, geometry2 blob)
int ST_CoveredBy(geometry1 blob, geometry2 blob)

