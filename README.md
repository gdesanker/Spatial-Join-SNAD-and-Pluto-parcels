# Spatial-Join-SNAD-and-Pluto-parcels
--create table where SNAD parcels and pluto parcels overlap/intersect. Using bbl


--spatial intersect of SNAD and Pluto

--CREATE TABLE results_scratch.snad_parcels_bbl_gkd AS

select bbl, borough, ct2010, lotarea, bldgarea, spdist1, spdist2, spdist3, sdlbl, mappluto_citywide17v1x1.geom_2263 from admin.mappluto_citywide17v1x1, zoninglayers.specialpurpose where
    st_intersects(mappluto_citywide17v1x1.geom_2263, specialpurpose.geom_2263) and ownertype='P' and sdname like 'Special Natural Area District';

   
-- in QGIS, join snad_parcels_bbl_gkd with lc_2010_parcel_17x1x1_Correct

-- so will have TC pixel count for each SNAD parcel
