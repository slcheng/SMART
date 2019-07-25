HDD/SSD Real-Life Reliability Test
==================================

This is a project to estimate reliability of HDD/SSD drives in real-life conditions by
the analysis of SMART data collected by Linux users at https://linux-hardware.org. The
primary aim of the project is to find drives with longest "power on hours" and minimal
number of errors.

Everyone can contribute to this report by uploading probes of their computers by
the [hw-probe](https://github.com/linuxhw/hw-probe) tool:

    sudo hw-probe -all -upload

Total drives: 28202.

Contents
--------

1. [ About         ](#about)
2. [ HDD by Model  ](#hdd-by-model)
3. [ HDD by Family ](#hdd-by-family)
4. [ HDD by Vendor ](#hdd-by-vendor)
5. [ SSD by Model  ](#ssd-by-model)
6. [ SSD by Family ](#ssd-by-family)
7. [ SSD by Vendor ](#ssd-by-vendor)

About
-----

The structure of the reports directory is the following:

    {KIND OF DRIVE}/{VENDOR}/{MODEL PREFIX}/{MODEL}/{DRIVE ID}

    ( e.g. HDD/Seagate/ST1000/ST1000LM035-1RK172/3F1554E2F97E )

Based on SMART data we determine most reliable drive models and vendors by the
following formula:

    Rating = MAX( Power_On_Hours / ( 1 + Number_Of_Important_Errors ) ) / ( 365*24 )

    ( i.e. Rating = "Years before/between errors" )

Number_Of_Important_Errors — number of important errors that can indicate a drive failure:

* Current_Pending_Sector
* ECC_Uncorr_Error_Count
* End-to-End_Error
* Offline_Uncorrectable
* Reallocated_Event_Count
* Reallocated_Sector_Ct
* Reported_Uncorrect
* Soft_Read_Error_Rate
* Spin_Retry_Count
* Total_Pending_Sectors
* Unc_Soft_Read_Err_Rate

The list of important SMART attributes is taken from recent studies of Google [1] and
Backblaze [2]. If an attribute exceeds the value of 1000 then it's counted as '1000 +
log10(X - 999)'.

The list of tracked attributes and rating calculation method can be discussed. Please
suggest your ideas in "issues".

You can perform your own analysis of collected reports if needed.

* [1] Google, "Failure Trends in a Large Disk Drive Population" (https://research.google.com/archive/disk_failures.pdf)
* [2] Backblaze, "Hard Drive SMART Stats" (https://www.backblaze.com/blog/hard-drive-smart-stats/)

HDD by Model
------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

See complete list of tested HDD samples in the Appendix 1 (All_HDD.md).

| MFG       | Model              | Size   | Samples | Days  | Err   | Rating |
|-----------|--------------------|--------|---------|-------|-------|--------|
| Samsung   | SV1021H            | 10 GB  | 1       | 5713  | 0     | 15.65  |
| Hitachi   | HDS728040PLA320... | 40 GB  | 1       | 3563  | 0     | 9.76   |
| WDC       | WD1600JD-00HBC0    | 160 GB | 1       | 3315  | 0     | 9.08   |
| WDC       | WD10EAVS-32D7B1    | 1 TB   | 1       | 3311  | 0     | 9.07   |
| WDC       | WD10EACS-00C7B0    | 1 TB   | 2       | 3164  | 0     | 8.67   |
| Samsung   | HE160HJ            | 160 GB | 1       | 2967  | 0     | 8.13   |
| WDC       | WD1200JB-00REA0    | 120 GB | 1       | 2899  | 0     | 7.94   |
| WDC       | WD740GD-00FLA1     | 74 GB  | 1       | 2489  | 0     | 6.82   |
| WDC       | WD2500YS-01SHB0    | 256 GB | 1       | 2484  | 0     | 6.81   |
| WDC       | WD400JB-00ENA0     | 40 GB  | 2       | 2923  | 6     | 6.74   |
| WDC       | WD5001AALS-00J7B0  | 500 GB | 1       | 2295  | 0     | 6.29   |
| Fujitsu   | MHV2040BH          | 40 GB  | 1       | 2224  | 0     | 6.09   |
| WDC       | WD2500AAJS-07VWA0  | 250 GB | 2       | 2219  | 0     | 6.08   |
| Seagate   | ST3750641NS        | 752 GB | 1       | 2169  | 0     | 5.94   |
| WDC       | WD2500AAJS-61B4A0  | 250 GB | 1       | 2168  | 0     | 5.94   |
| WDC       | WD2002FYPS-01U1B0  | 2 TB   | 1       | 2163  | 0     | 5.93   |
| WDC       | WD1001FALS-00K1B0  | 1 TB   | 2       | 2132  | 0     | 5.84   |
| HP        | GB0250EAFYK        | 250 GB | 1       | 2025  | 0     | 5.55   |
| Seagate   | ST3500641AS        | 500 GB | 1       | 1996  | 0     | 5.47   |
| WDC       | WD1600AABS-61PRA0  | 160 GB | 1       | 1982  | 0     | 5.43   |
| WDC       | WD1601ABYS-01C0A0  | 164 GB | 1       | 1982  | 0     | 5.43   |
| WDC       | WD1600AAJS-00RYA0  | 160 GB | 1       | 1970  | 0     | 5.40   |
| WDC       | WD2003FYPS-27Y2B0  | 2 TB   | 5       | 2163  | 1     | 5.29   |
| Samsung   | HE103SJ            | 1 TB   | 1       | 1865  | 0     | 5.11   |
| WDC       | WD7500AAKS-22RBA0  | 752 GB | 1       | 1816  | 0     | 4.98   |
| WDC       | WD360GD-00FNA0     | 37 GB  | 2       | 2599  | 1     | 4.95   |
| WDC       | WD2500YS-70SHB1    | 250 GB | 1       | 1789  | 0     | 4.90   |
| Hitachi   | HUA721050KLA330    | 500 GB | 2       | 1774  | 0     | 4.86   |
| HGST      | HUS724020ALE640    | 2 TB   | 7       | 1736  | 0     | 4.76   |
| WDC       | WD2500KS-22MJB0    | 250 GB | 1       | 1734  | 0     | 4.75   |
| Seagate   | ST960813AS         | 64 GB  | 1       | 1729  | 0     | 4.74   |
| WDC       | WD4000AAJS-22YFA0  | 400 GB | 1       | 1725  | 0     | 4.73   |
| WDC       | WD5000ABYS-01TNA0  | 500 GB | 1       | 1707  | 0     | 4.68   |
| HGST      | HTE541515A9E630    | 1.5 TB | 1       | 1702  | 0     | 4.66   |
| WDC       | WD5000BMVV-11GNWS0 | 500 GB | 1       | 1671  | 0     | 4.58   |
| WDC       | WD1600JS-88MHB0    | 160 GB | 1       | 1667  | 0     | 4.57   |
| WDC       | WD3200AAJS-22RYA0  | 320 GB | 3       | 1653  | 0     | 4.53   |
| HP        | FB080C4080         | 80 GB  | 1       | 1630  | 0     | 4.47   |
| Maxtor    | 6V300F0            | 304 GB | 1       | 1613  | 0     | 4.42   |
| WDC       | WD2000JB-16FUA0    | 200 GB | 1       | 1584  | 0     | 4.34   |
| WDC       | WD3200AAVS-00ZTB0  | 320 GB | 1       | 1583  | 0     | 4.34   |
| WDC       | WD2502ABYS-01B7A0  | 256 GB | 2       | 1576  | 0     | 4.32   |
| WDC       | WD4000AAJS-65TKA0  | 400 GB | 1       | 1532  | 0     | 4.20   |
| WDC       | WD2502ABYS-23B7... | 250 GB | 2       | 1522  | 0     | 4.17   |
| HP        | GB1000EAMYC        | 1 TB   | 1       | 1490  | 0     | 4.08   |
| WDC       | WD2000JD-00GBB0    | 200 GB | 1       | 1482  | 0     | 4.06   |
| WDC       | WD1200JS-55NCB1    | 120 GB | 1       | 1469  | 0     | 4.03   |
| WDC       | WD800JD-75MSA2     | 79 GB  | 1       | 1432  | 0     | 3.92   |
| Hitachi   | HDT722520DLAT80    | 200 GB | 2       | 1406  | 0     | 3.85   |
| Hitachi   | HUA723030ALA640    | 3 TB   | 1       | 1403  | 0     | 3.84   |
| WDC       | WD2500JB-22REA0    | 250 GB | 1       | 1398  | 0     | 3.83   |
| WDC       | WD2001FASS-00W2B0  | 2 TB   | 1       | 1392  | 0     | 3.82   |
| HP        | MB2000GCWDA        | 2 TB   | 1       | 1370  | 0     | 3.76   |
| WDC       | WD1500HLFS-01G6U0  | 150 GB | 3       | 1403  | 1     | 3.75   |
| WDC       | WD2500AAJS-22RYA0  | 250 GB | 1       | 1365  | 0     | 3.74   |
| WDC       | WD7500BPVT-80HXZT1 | 752 GB | 1       | 1360  | 0     | 3.73   |
| WDC       | WD3200AAJB-00WGA0  | 320 GB | 2       | 1356  | 0     | 3.72   |
| WDC       | WD2500JS-00MHB0    | 250 GB | 4       | 1325  | 0     | 3.63   |
| WDC       | WD20EADS-00S2B0    | 2 TB   | 1       | 1315  | 0     | 3.60   |
| Fujitsu   | MPE3064AT          | 6 GB   | 2       | 1315  | 0     | 3.60   |
| WDC       | WD2000FYYZ-01UL1B2 | 2 TB   | 2       | 1314  | 0     | 3.60   |
| WDC       | WD7500AYYS-01RCA0  | 752 GB | 4       | 1405  | 1     | 3.59   |
| WDC       | WD2500AAKX-08ERMA0 | 250 GB | 1       | 1306  | 0     | 3.58   |
| WDC       | WD1200BB-00GUA0    | 120 GB | 1       | 1284  | 0     | 3.52   |
| Hitachi   | HCS5C3232SLA380    | 320 GB | 1       | 1281  | 0     | 3.51   |
| WDC       | WD4000AAKS-00A7B0  | 400 GB | 1       | 1280  | 0     | 3.51   |
| WDC       | WD15EVDS-68V9B0    | 1.5 TB | 1       | 1276  | 0     | 3.50   |
| WDC       | WD800JD-08LSA0     | 80 GB  | 8       | 1428  | 3     | 3.47   |
| Samsung   | SP0451N            | 40 GB  | 1       | 1237  | 0     | 3.39   |
| WDC       | WD6400AACS-00G8B0  | 640 GB | 2       | 1216  | 0     | 3.33   |
| WDC       | WD1200JD-00HBB0    | 120 GB | 5       | 1411  | 3     | 3.32   |
| Hitachi   | HDS721075KLA330    | 752 GB | 7       | 1493  | 14    | 3.31   |
| Hitachi   | HDT721075SLA380    | 752 GB | 1       | 1205  | 0     | 3.30   |
| Seagate   | ST3160828AS        | 160 GB | 1       | 1198  | 0     | 3.28   |
| WDC       | WD5000AAJS-32YFA0  | 500 GB | 1       | 1187  | 0     | 3.25   |
| Seagate   | ST3300631A         | 304 GB | 1       | 1185  | 0     | 3.25   |
| WDC       | WD1001FALS-40U9B0  | 1 TB   | 1       | 1175  | 0     | 3.22   |
| WDC       | WD3200AAJB-56WGA0  | 320 GB | 3       | 1172  | 0     | 3.21   |
| Seagate   | ST3320620NS        | 320 GB | 3       | 1312  | 1     | 3.20   |
| WDC       | WD3200AAJS-07RYA0  | 320 GB | 1       | 1168  | 0     | 3.20   |
| WDC       | WD1500AHFD-00RAR5  | 150 GB | 1       | 1164  | 0     | 3.19   |
| WDC       | WD5000AVJB-63YUA0  | 500 GB | 1       | 1163  | 0     | 3.19   |
| Toshiba   | MK8017GSG          | 80 GB  | 1       | 1162  | 0     | 3.18   |
| WDC       | WD2500AAKS-22VSA0  | 250 GB | 1       | 1161  | 0     | 3.18   |
| Samsung   | HD400LD            | 400 GB | 2       | 1157  | 0     | 3.17   |
| WDC       | WD2503ABYX-01WERA0 | 256 GB | 1       | 1155  | 0     | 3.16   |
| Seagate   | ST3250823AS        | 250 GB | 10      | 1321  | 25    | 3.16   |
| WDC       | WD1500HLFS-01G6U3  | 150 GB | 1       | 1145  | 0     | 3.14   |
| WDC       | WD800JD-00HKA0     | 80 GB  | 2       | 1144  | 0     | 3.14   |
| Seagate   | ST3400832AS        | 400 GB | 1       | 3418  | 2     | 3.12   |
| Seagate   | ST160LM003 HN-M... | 160 GB | 1       | 1139  | 0     | 3.12   |
| WDC       | WD3200AAKS-00G3A0  | 320 GB | 5       | 1137  | 0     | 3.12   |
| WDC       | WD1600JS-55MHB1    | 160 GB | 2       | 1135  | 0     | 3.11   |
| WDC       | WD5003AZEX-00RKKA0 | 500 GB | 2       | 1135  | 0     | 3.11   |
| Toshiba   | MG03ACA200         | 2 TB   | 1       | 1134  | 0     | 3.11   |
| WDC       | WD5001ABYS-01YNA0  | 500 GB | 1       | 1126  | 0     | 3.09   |
| Seagate   | ST3320820AS_Q      | 320 GB | 1       | 1125  | 0     | 3.08   |
| WDC       | WD20EARS-07MVWB0   | 2 TB   | 3       | 1807  | 1     | 3.08   |
| Fujitsu   | MHW2060BH          | 64 GB  | 1       | 1118  | 0     | 3.06   |
| WDC       | WD3200AAJB-00TYA0  | 320 GB | 3       | 1118  | 0     | 3.06   |
| WDC       | WD3200AAJS-40VWA0  | 320 GB | 1       | 1118  | 0     | 3.06   |
| WDC       | WD7500AACS-00D6B0  | 752 GB | 1       | 1107  | 0     | 3.03   |
| Hitachi   | HDS7250SASUN500... | 500 GB | 1       | 1103  | 0     | 3.02   |
| WDC       | WD1200JS-00SGB0    | 120 GB | 2       | 1091  | 0     | 2.99   |
| WDC       | WD1001FALS-00J7B0  | 1 TB   | 10      | 1087  | 0     | 2.98   |
| WDC       | WD30EFRX-68AX9N0   | 3 TB   | 8       | 1225  | 2     | 2.97   |
| Seagate   | ST9500620NS 81Y... | 500 GB | 1       | 1083  | 0     | 2.97   |
| WDC       | WD7500AARX-00N0YB0 | 752 GB | 1       | 1081  | 0     | 2.96   |
| WDC       | WD30EURX-64HYZY0   | 3 TB   | 1       | 1077  | 0     | 2.95   |
| Maxtor    | 7V250F0            | 256 GB | 2       | 1075  | 0     | 2.95   |
| WDC       | WD1600YS-01SHB1    | 164 GB | 6       | 1060  | 0     | 2.91   |
| WDC       | WD6400AACS-00D6B1  | 640 GB | 1       | 1058  | 0     | 2.90   |
| Seagate   | ST3400620A         | 400 GB | 3       | 1802  | 61    | 2.88   |
| WDC       | WD2500JS-00MHB1    | 250 GB | 2       | 1052  | 0     | 2.88   |
| HGST      | MB6000GEBTP        | 6 TB   | 1       | 1046  | 0     | 2.87   |
| WDC       | WD3200JD-00KLB0    | 320 GB | 1       | 1045  | 0     | 2.87   |
| Samsung   | HD160JJ-P          | 160 GB | 7       | 1513  | 436   | 2.84   |
| WDC       | WD800BB-75FRA0     | 80 GB  | 2       | 1034  | 0     | 2.83   |
| Seagate   | ST340823A          | 40 GB  | 1       | 1034  | 0     | 2.83   |
| WDC       | WD1600JB-00REA0    | 160 GB | 8       | 1147  | 4     | 2.83   |
| Samsung   | HD040GJ            | 40 GB  | 3       | 1360  | 41    | 2.82   |
| Hitachi   | HDS721016CLA382    | 160 GB | 5       | 1062  | 1     | 2.82   |
| WDC       | WD800BB-22JHA0     | 80 GB  | 2       | 1029  | 0     | 2.82   |
| WDC       | WD1001FALS-403AA0  | 1 TB   | 2       | 1025  | 0     | 2.81   |
| Hitachi   | HDS722020ALA330    | 2 TB   | 14      | 1448  | 6     | 2.81   |
| WDC       | WD800AAJS-75M0A0   | 80 GB  | 2       | 1114  | 4     | 2.81   |
| Hitachi   | HDT725040VLA360    | 400 GB | 2       | 1024  | 0     | 2.81   |
| WDC       | WD2500JB-57REA0    | 250 GB | 1       | 1021  | 0     | 2.80   |
| WDC       | WD400LB-00DNA0     | 40 GB  | 2       | 1103  | 2     | 2.78   |
| WDC       | WD200BB-00DEA0     | 20 GB  | 1       | 1015  | 0     | 2.78   |
| Hitachi   | HUA723020ALA640    | 2 TB   | 10      | 1014  | 0     | 2.78   |
| WDC       | WD1600JB-00EVA0    | 160 GB | 1       | 1012  | 0     | 2.77   |
| Toshiba   | MC04ACA200E        | 2 TB   | 1       | 1008  | 0     | 2.76   |
| Seagate   | ST320LT023-1AF142  | 320 GB | 1       | 1007  | 0     | 2.76   |
| Hitachi   | HDS723020BLA642    | 2 TB   | 26      | 1221  | 48    | 2.75   |
| WDC       | WD2000JS-22MHB0    | 200 GB | 3       | 2210  | 13    | 2.74   |
| Hitachi   | HDT725032VLA380    | 320 GB | 7       | 1356  | 139   | 2.73   |
| WDC       | WD1000FYPS-01ZKB0  | 1 TB   | 1       | 989   | 0     | 2.71   |
| WDC       | WD20NMVW-11AV3S2   | 2 TB   | 5       | 1029  | 1     | 2.69   |
| WDC       | WD3200AAKX-221CA0  | 320 GB | 1       | 981   | 0     | 2.69   |
| WDC       | WD2500BEVS-00UST0  | 250 GB | 1       | 981   | 0     | 2.69   |
| WDC       | WD400JB-00JJC0     | 40 GB  | 1       | 980   | 0     | 2.69   |
| WDC       | WD20EARX-008FB0    | 2 TB   | 4       | 978   | 0     | 2.68   |
| Samsung   | HD040GJ-P          | 40 GB  | 1       | 975   | 0     | 2.67   |
| WDC       | WD4000AAKS-00YGA0  | 400 GB | 5       | 1166  | 1     | 2.67   |
| WDC       | WD5000AAKS-07YGA0  | 500 GB | 3       | 971   | 0     | 2.66   |
| WDC       | WD20EARX-22PASB0   | 2 TB   | 2       | 964   | 0     | 2.64   |
| WDC       | WD2500AAJS-22VWA0  | 250 GB | 1       | 961   | 0     | 2.63   |
| Seagate   | ST3250820SCE       | 250 GB | 2       | 960   | 0     | 2.63   |
| WDC       | WD2000JS-00MVB1    | 200 GB | 1       | 957   | 0     | 2.62   |
| WDC       | WD7502AAEX-00Z3A0  | 752 GB | 1       | 956   | 0     | 2.62   |
| Hitachi   | HDS5C1010CLA382    | 1 TB   | 7       | 954   | 0     | 2.61   |
| Hitachi   | HDS5C3030ALA630    | 3 TB   | 2       | 1454  | 1     | 2.60   |
| WDC       | WD10EACS-00D6B0    | 1 TB   | 5       | 1219  | 2     | 2.60   |
| Quantum   | FIREBALLP AS20.5   | 20 GB  | 1       | 946   | 0     | 2.59   |
| WDC       | WD10EADS-65M2B1    | 1 TB   | 1       | 946   | 0     | 2.59   |
| WDC       | WD2500JS-22NCB1    | 250 GB | 6       | 1088  | 1     | 2.59   |
| WDC       | WD30EZRX-00DC0B0   | 3 TB   | 9       | 942   | 0     | 2.58   |
| WDC       | WD10EADS-11M2B3    | 1 TB   | 2       | 940   | 0     | 2.58   |
| Seagate   | ST250LT020-1AE14C  | 250 GB | 1       | 936   | 0     | 2.57   |
| WDC       | WD1600JS-55NCB1    | 160 GB | 4       | 935   | 0     | 2.56   |
| WDC       | WD5000AAKB-00YSA0  | 500 GB | 2       | 935   | 0     | 2.56   |
| WDC       | WD5000LUCT-63C26Y0 | 500 GB | 1       | 934   | 0     | 2.56   |
| WDC       | WD800JB-00DUA3     | 80 GB  | 1       | 923   | 0     | 2.53   |
| WDC       | WD1600AAJS-07WAA0  | 160 GB | 4       | 1371  | 213   | 2.53   |
| Hitachi   | HDS5C3015ALA632    | 1.5 TB | 2       | 1186  | 160   | 2.51   |
| WDC       | WD3200AAKX-603CA0  | 320 GB | 1       | 914   | 0     | 2.51   |
| Seagate   | ST3300622A         | 304 GB | 1       | 912   | 0     | 2.50   |
| WDC       | WD10EACS-00D6B1    | 1 TB   | 3       | 1891  | 101   | 2.49   |
| WDC       | WD15EARS-00J2GB0   | 1.5 TB | 1       | 908   | 0     | 2.49   |
| WDC       | WD10EACS-00ZJB0    | 1 TB   | 3       | 908   | 0     | 2.49   |
| HGST      | HDN724040ALE640    | 4 TB   | 8       | 906   | 0     | 2.48   |
| WDC       | WD2500JS-60NCB1    | 250 GB | 6       | 1017  | 1     | 2.48   |
| Seagate   | ST3400833AS        | 400 GB | 1       | 905   | 0     | 2.48   |
| Seagate   | ST4000VN000-1H4168 | 4 TB   | 15      | 997   | 135   | 2.48   |
| Seagate   | ST3300831AS        | 304 GB | 2       | 1451  | 4     | 2.48   |
| WDC       | WD2500AAKX-75U6AA0 | 250 GB | 1       | 902   | 0     | 2.47   |
| WDC       | WD400BB-71DGA0     | 40 GB  | 1       | 900   | 0     | 2.47   |
| Seagate   | ST3802110AS        | 80 GB  | 2       | 899   | 0     | 2.46   |
| WDC       | WD740ADFD-00NLR1   | 74 GB  | 1       | 895   | 0     | 2.45   |
| Hitachi   | HTS545032B9SA00    | 320 GB | 4       | 1033  | 516   | 2.44   |
| WDC       | WD800BB-22HEA1     | 80 GB  | 1       | 888   | 0     | 2.43   |
| WDC       | WD1600BB-56RDA0    | 160 GB | 2       | 888   | 0     | 2.43   |
| HGST      | HTE541010A9E680    | 1 TB   | 2       | 913   | 509   | 2.43   |
| WDC       | WD2500AAJS-55RYA0  | 250 GB | 2       | 887   | 0     | 2.43   |
| WDC       | WD1600JS-60MHB1    | 160 GB | 6       | 1053  | 4     | 2.43   |
| WDC       | WD4000KS-00MNB0    | 400 GB | 3       | 883   | 0     | 2.42   |
| Seagate   | ST91000640NS 81... | 1 TB   | 1       | 883   | 0     | 2.42   |
| WDC       | WD6400AAKS-00A7B2  | 640 GB | 5       | 882   | 0     | 2.42   |
| WDC       | WD2500AAJS-75VWA0  | 250 GB | 1       | 880   | 0     | 2.41   |
| WDC       | WD1600AAJS-75WAA0  | 160 GB | 2       | 880   | 0     | 2.41   |
| WDC       | WD3200BEVE-00A0HT0 | 320 GB | 2       | 877   | 0     | 2.40   |
| Hitachi   | HDT722520DLA380    | 200 GB | 4       | 1091  | 2     | 2.40   |
| Toshiba   | MQ01ABF050H        | 500 GB | 2       | 873   | 0     | 2.39   |
| WDC       | WD5000AACS-00ZUB0  | 500 GB | 9       | 911   | 1     | 2.39   |
| Seagate   | ST360021A          | 64 GB  | 3       | 868   | 0     | 2.38   |
| WDC       | WD1600BEVS-08VAT2  | 160 GB | 5       | 957   | 1     | 2.37   |
| WDC       | WD800BB-75JHA0     | 79 GB  | 1       | 865   | 0     | 2.37   |
| WDC       | WD1600AAJS-22PSA0  | 160 GB | 13      | 964   | 4     | 2.37   |
| WDC       | WD3202ABYS-02B7A0  | 320 GB | 6       | 929   | 1     | 2.36   |
| WDC       | WD800AAJS-22PSA0   | 80 GB  | 4       | 852   | 0     | 2.33   |
| Seagate   | ST3500630A         | 500 GB | 7       | 1381  | 33    | 2.33   |
| Hitachi   | HCS5C1050CLA382    | 500 GB | 1       | 848   | 0     | 2.33   |
| WDC       | WD5000AAKS-00TMA0  | 500 GB | 5       | 995   | 3     | 2.32   |
| WDC       | WD10EADS-00L5B1    | 1 TB   | 28      | 1247  | 4     | 2.31   |
| WDC       | WD2500JS-55NCB1    | 250 GB | 2       | 1144  | 16    | 2.30   |
| WDC       | WD2500YS-01SHB1    | 250 GB | 6       | 999   | 1     | 2.29   |
| WDC       | WD800BB-00DKA0     | 80 GB  | 3       | 977   | 1     | 2.29   |
| Seagate   | ST4000VN0001-1S... | 4 TB   | 1       | 836   | 0     | 2.29   |
| WDC       | WD10EALX-089BA0    | 1 TB   | 2       | 836   | 0     | 2.29   |
| WDC       | WD7501AALS-00J7B1  | 752 GB | 8       | 1052  | 1     | 2.28   |
| Seagate   | ST3750840AS        | 752 GB | 1       | 828   | 0     | 2.27   |
| WDC       | WD6400AAKS-00A7B0  | 640 GB | 11      | 1003  | 4     | 2.27   |
| WDC       | WD400BB-00DEA0     | 40 GB  | 1       | 825   | 0     | 2.26   |
| WDC       | WD800BD-88JMC0     | 80 GB  | 2       | 824   | 0     | 2.26   |
| WDC       | WD1003FZEX-00RLFA0 | 1 TB   | 2       | 823   | 0     | 2.26   |
| Hitachi   | HDS728040PLAT20    | 41 GB  | 5       | 979   | 1     | 2.25   |
| WDC       | WD1600JB-00GVA0    | 160 GB | 1       | 822   | 0     | 2.25   |
| WDC       | WD1200JB-00EVA0    | 120 GB | 3       | 821   | 0     | 2.25   |
| WDC       | WD6401AALS-00L3B2  | 640 GB | 16      | 1176  | 6     | 2.25   |
| WDC       | WD800JD-75MSA3     | 80 GB  | 17      | 945   | 1     | 2.24   |
| WDC       | WD5000AAKS-00YGA0  | 500 GB | 17      | 1040  | 4     | 2.24   |
| WDC       | WD2500BEVE-00WZT0  | 250 GB | 2       | 817   | 0     | 2.24   |
| WDC       | WD400BB-00LNA0     | 40 GB  | 1       | 817   | 0     | 2.24   |
| Hitachi   | HDT725050VLA380    | 500 GB | 2       | 1307  | 19    | 2.24   |
| WDC       | WD5000HHTZ-04N21V0 | 500 GB | 4       | 813   | 0     | 2.23   |
| WDC       | WD1500HLFS-01G6U1  | 150 GB | 3       | 813   | 0     | 2.23   |
| WDC       | WD2500JB-00GVC0    | 250 GB | 2       | 811   | 0     | 2.22   |
| HGST      | HUS726040ALA610    | 4 TB   | 2       | 810   | 0     | 2.22   |
| WDC       | WD10EALX-759BA1    | 1 TB   | 5       | 1376  | 5     | 2.21   |
| Seagate   | ST3120213AS        | 120 GB | 1       | 806   | 0     | 2.21   |
| WDC       | WD3200AAKS-22B3A0  | 320 GB | 1       | 806   | 0     | 2.21   |
| Seagate   | ST3320413AS        | 320 GB | 7       | 1178  | 4     | 2.21   |
| Hitachi   | HTS723232L9SA62    | 320 GB | 1       | 804   | 0     | 2.20   |
| WDC       | WD7500AALX-009BA0  | 752 GB | 6       | 798   | 0     | 2.19   |
| WDC       | WD3200AAKS-75SBA0  | 320 GB | 1       | 798   | 0     | 2.19   |
| WDC       | WD800JD-60LSA5     | 80 GB  | 14      | 852   | 2     | 2.18   |
| WDC       | WD1600JS-75NCB3    | 160 GB | 3       | 794   | 0     | 2.18   |
| WDC       | WD7500AAKS-00RBA0  | 752 GB | 6       | 920   | 84    | 2.18   |
| WDC       | WD3003FZEX-00Z4SA0 | 3 TB   | 1       | 793   | 0     | 2.17   |
| WDC       | WD5000BPKX-75HPJT0 | 500 GB | 2       | 787   | 0     | 2.16   |
| HGST      | HDN726060ALE610    | 6 TB   | 1       | 787   | 0     | 2.16   |
| Seagate   | ST6000DM001-1XY17Z | 6 TB   | 1       | 783   | 0     | 2.15   |
| Seagate   | ST6000VN0021-1Z... | 6 TB   | 1       | 783   | 0     | 2.15   |
| WDC       | WD3200BEKT-75PVMT1 | 320 GB | 2       | 782   | 0     | 2.14   |
| WDC       | WD6001FFWX-68Z39N0 | 6 TB   | 1       | 782   | 0     | 2.14   |
| WDC       | WD6400AAKS-75A7B2  | 640 GB | 3       | 1059  | 3     | 2.14   |
| WDC       | WD5000AADS-56S9B0  | 500 GB | 1       | 782   | 0     | 2.14   |
| Seagate   | ST91603110CS       | 160 GB | 1       | 781   | 0     | 2.14   |
| WDC       | WD5000AAKS-65YGA0  | 500 GB | 7       | 780   | 0     | 2.14   |
| WDC       | WD5001AALS-00E3A0  | 500 GB | 9       | 776   | 0     | 2.13   |
| WDC       | WD10EARX-32N0YB0   | 1 TB   | 3       | 799   | 5     | 2.13   |
| WDC       | WD2500BB-00GUA0    | 250 GB | 1       | 773   | 0     | 2.12   |
| WDC       | WD2500JS-60NCB2    | 250 GB | 2       | 773   | 0     | 2.12   |
| WDC       | WD2500JS-00NCB1    | 250 GB | 10      | 1117  | 34    | 2.12   |
| Hitachi   | HTS723225L9A362    | 250 GB | 1       | 770   | 0     | 2.11   |
| WDC       | WD1600AAJS-07PSA0  | 160 GB | 3       | 1618  | 9     | 2.10   |
| WDC       | WD10EALS-002BA0    | 1 TB   | 3       | 766   | 0     | 2.10   |
| Hitachi   | HTS722012K9SA00    | 120 GB | 3       | 851   | 340   | 2.10   |
| WDC       | WD3200AAKX-083CA1  | 320 GB | 1       | 763   | 0     | 2.09   |
| WDC       | WD7501AALS-00E8B0  | 752 GB | 4       | 1396  | 4     | 2.09   |
| WDC       | WD5000BMVW-11AMCS4 | 500 GB | 1       | 762   | 0     | 2.09   |
| WDC       | WD2500JD-55HBB0    | 250 GB | 2       | 1468  | 16    | 2.07   |
| WDC       | WD3000JS-19PDB0    | 304 GB | 1       | 751   | 0     | 2.06   |
| WDC       | WD400BB-60JKA0     | 40 GB  | 2       | 746   | 0     | 2.04   |
| Quantum   | FIREBALLP AS40.0   | 40 GB  | 1       | 744   | 0     | 2.04   |
| Fujitsu   | MHV2060AH PL       | 52 GB  | 1       | 741   | 0     | 2.03   |
| WDC       | WD2500AAKX-60U6AA0 | 250 GB | 2       | 733   | 0     | 2.01   |
| WDC       | WD1600AAJS-60PSA0  | 160 GB | 4       | 904   | 257   | 2.01   |
| WDC       | WD2500AAJS-75M0A0  | 250 GB | 2       | 728   | 0     | 2.00   |
| WDC       | WD2500AAKX-221CA1  | 250 GB | 2       | 1139  | 4     | 1.99   |
| Seagate   | ST1000VX001-1Z4102 | 1 TB   | 1       | 725   | 0     | 1.99   |
| WDC       | WD2500AAJS-00VTA0  | 250 GB | 20      | 858   | 79    | 1.98   |
| WDC       | WD3200BEVT-75ZCT2  | 320 GB | 2       | 720   | 0     | 1.98   |
| Fujitsu   | MHV2100AH          | 100 GB | 2       | 719   | 0     | 1.97   |
| WDC       | WD6402AAEX-00Z3A0  | 640 GB | 3       | 719   | 0     | 1.97   |
| Seagate   | ST8000AS0002-1N... | 8 TB   | 1       | 718   | 0     | 1.97   |
| Seagate   | ST310211A          | 10 GB  | 1       | 716   | 0     | 1.96   |
| WDC       | WD1502FAEX-007BA0  | 1.5 TB | 5       | 816   | 35    | 1.96   |
| Seagate   | ST32000644NS       | 2 TB   | 2       | 716   | 1     | 1.96   |
| HGST      | HUS724030ALA640    | 3 TB   | 6       | 896   | 4     | 1.95   |
| Hitachi   | HUA722020ALA331    | 2 TB   | 3       | 801   | 2     | 1.95   |
| WDC       | WD1600JS-58NCB1    | 160 GB | 1       | 712   | 0     | 1.95   |
| WDC       | WD1002FAEX-00Y9A0  | 1 TB   | 31      | 805   | 24    | 1.95   |
| Samsung   | HD300LJ            | 304 GB | 7       | 1073  | 487   | 1.95   |
| Seagate   | ST1000VM002-9ZL162 | 1 TB   | 1       | 709   | 0     | 1.95   |
| WDC       | WD200BB-32CFC0     | 20 GB  | 1       | 709   | 0     | 1.94   |
| WDC       | WD800AAJS-22WAA0   | 80 GB  | 1       | 708   | 0     | 1.94   |
| ExcelStor | J9250S             | 250 GB | 4       | 707   | 0     | 1.94   |
| WDC       | WD1600BEVS-22UST0  | 160 GB | 2       | 997   | 95    | 1.93   |
| WDC       | WD800JD-00LSA0     | 80 GB  | 20      | 990   | 11    | 1.93   |
| WDC       | WD1600AAJS-22WAA0  | 160 GB | 2       | 1063  | 2     | 1.92   |
| WDC       | WD3200AAJS-65B4A0  | 320 GB | 1       | 699   | 0     | 1.92   |
| Hitachi   | HDS5C3020ALA632    | 2 TB   | 13      | 828   | 3     | 1.91   |
| Seagate   | ST3250620NS        | 250 GB | 15      | 1016  | 327   | 1.91   |
| WDC       | WD2500AAKX-753CA1  | 250 GB | 6       | 704   | 2     | 1.91   |
| WDC       | WD6400BPVT-35HXZT1 | 640 GB | 2       | 696   | 0     | 1.91   |
| WDC       | WD2500LPVT-00G33T0 | 250 GB | 1       | 696   | 0     | 1.91   |
| Seagate   | ST3300620AS        | 304 GB | 1       | 692   | 0     | 1.90   |
| WDC       | WD6400AAKS-65A7B0  | 640 GB | 5       | 787   | 3     | 1.89   |
| WDC       | WD2500BEKT-75PVMT1 | 250 GB | 1       | 689   | 0     | 1.89   |
| Seagate   | ST2000VM003-1CT164 | 2 TB   | 4       | 845   | 1     | 1.89   |
| WDC       | WD5001AALS-00L3B2  | 500 GB | 30      | 986   | 31    | 1.89   |
| WDC       | WD10JMVW-11AJGS1   | 1 TB   | 1       | 688   | 0     | 1.89   |
| WDC       | WD1001FALS-00Y6A0  | 1 TB   | 4       | 936   | 28    | 1.88   |
| Seagate   | ST340215AS         | 40 GB  | 1       | 686   | 0     | 1.88   |
| Fujitsu   | MHZ2080BH G2       | 80 GB  | 1       | 684   | 0     | 1.88   |
| Seagate   | ST31500541AS       | 1.5 TB | 8       | 918   | 46    | 1.87   |
| WDC       | WD1001FALS-00J7B1  | 1 TB   | 12      | 884   | 3     | 1.87   |
| WDC       | WD5000AUDX-63WNHY0 | 500 GB | 2       | 680   | 0     | 1.86   |
| Hitachi   | HUA721010KLA330... | 1 TB   | 1       | 2715  | 3     | 1.86   |
| Seagate   | ST4000DM000-1F2168 | 4 TB   | 18      | 689   | 1     | 1.86   |
| WDC       | WD800BB-63JKC0     | 80 GB  | 1       | 676   | 0     | 1.85   |
| WDC       | WD2000F9YZ-09N20L0 | 2 TB   | 1       | 675   | 0     | 1.85   |
| WDC       | WD15EARS-22Z5B1    | 1.5 TB | 3       | 675   | 0     | 1.85   |
| WDC       | WD5000LPVT-16G33T0 | 500 GB | 3       | 675   | 0     | 1.85   |
| WDC       | WD20EFRX-68AX9N0   | 2 TB   | 8       | 751   | 1     | 1.85   |
| WDC       | WD800BB-75DKA0     | 80 GB  | 1       | 672   | 0     | 1.84   |
| WDC       | WD2500KS-00MJB0    | 250 GB | 19      | 917   | 18    | 1.84   |
| WDC       | WD1200JS-55MHB0    | 120 GB | 2       | 671   | 0     | 1.84   |
| WDC       | WD5000LPVT-60G33T0 | 500 GB | 1       | 670   | 0     | 1.84   |
| WDC       | WD10EADS-00M2B0    | 1 TB   | 24      | 905   | 84    | 1.84   |
| WDC       | WD30EZRX-00MMMB0   | 3 TB   | 6       | 836   | 2     | 1.84   |
| WDC       | WD1502FYPS-01U1B1  | 1.5 TB | 1       | 667   | 0     | 1.83   |
| Hitachi   | HDT721016SLA380    | 160 GB | 13      | 788   | 5     | 1.82   |
| WDC       | WD30EURS-63R8UY0   | 3 TB   | 2       | 664   | 0     | 1.82   |
| Seagate   | ST4000VM000-1F3168 | 4 TB   | 5       | 663   | 0     | 1.82   |
| Seagate   | ST3320413CS        | 320 GB | 8       | 730   | 141   | 1.82   |
| WDC       | WD3000HLFS-01G6U4  | 304 GB | 1       | 662   | 0     | 1.81   |
| WDC       | WD1200JD-00FYB0    | 120 GB | 1       | 661   | 0     | 1.81   |
| WDC       | WD2003FYYS-02W0B0  | 2 TB   | 3       | 757   | 1     | 1.80   |
| WDC       | WD1600AVBS-63SVA0  | 160 GB | 1       | 658   | 0     | 1.80   |
| WDC       | WD5000AAKS-00A7B0  | 500 GB | 22      | 1068  | 9     | 1.80   |
| WDC       | WD5000BPVT-75HXZT1 | 500 GB | 1       | 657   | 0     | 1.80   |
| Seagate   | ST3400620AS        | 400 GB | 21      | 1023  | 8     | 1.80   |
| WDC       | WD5000AAJS-00TKA0  | 500 GB | 1       | 656   | 0     | 1.80   |
| WDC       | WD2500AAKX-22ERMA0 | 250 GB | 1       | 656   | 0     | 1.80   |
| WDC       | WD1600JS-98NCB1    | 160 GB | 1       | 655   | 0     | 1.80   |
| Hitachi   | HTS723216L9SA60    | 160 GB | 2       | 654   | 0     | 1.79   |
| WDC       | WD5000AAKS-07V0A0  | 500 GB | 1       | 654   | 0     | 1.79   |
| WDC       | WD3200AAJS-65RYA0  | 320 GB | 2       | 652   | 0     | 1.79   |
| Seagate   | ST3000DM003-1F216N | 3 TB   | 1       | 652   | 0     | 1.79   |
| WDC       | WD5000AAKS-00Z7B0  | 500 GB | 1       | 652   | 0     | 1.79   |
| WDC       | WD400BD-60JPA0     | 40 GB  | 1       | 651   | 0     | 1.78   |
| WDC       | WD10EADS-65L5B1    | 1 TB   | 8       | 1190  | 4     | 1.78   |
| Hitachi   | HDS722580VLSA80    | 82 GB  | 3       | 1101  | 671   | 1.78   |
| WDC       | WD3200KS-00PFB0    | 320 GB | 2       | 1317  | 46    | 1.78   |
| WDC       | WD1200JS-00MHB0    | 120 GB | 12      | 690   | 1     | 1.77   |
| Seagate   | ST980812AS         | 80 GB  | 1       | 647   | 0     | 1.77   |
| WDC       | WD5000AAKS-07TMA0  | 500 GB | 1       | 646   | 0     | 1.77   |
| Hitachi   | HDT725025VLA380    | 250 GB | 11      | 895   | 46    | 1.77   |
| Seagate   | ST32000641AS       | 2 TB   | 9       | 821   | 179   | 1.77   |
| Seagate   | ST3320620AS        | 320 GB | 97      | 1087  | 251   | 1.77   |
| Toshiba   | DT01ABA050V        | 500 GB | 1       | 644   | 0     | 1.77   |
| WDC       | WD3200AAKS-00VYA0  | 320 GB | 6       | 734   | 59    | 1.76   |
| WDC       | WD5000AAKS-00C8A0  | 500 GB | 2       | 1045  | 93    | 1.76   |
| WDC       | WD1001FALS-19J7B0  | 1 TB   | 1       | 641   | 0     | 1.76   |
| Toshiba   | DT01ABA200V        | 2 TB   | 1       | 639   | 0     | 1.75   |
| WDC       | WD800JB-00ETA0     | 80 GB  | 5       | 1354  | 273   | 1.75   |
| WDC       | WD1600JS-98MHB0    | 160 GB | 1       | 638   | 0     | 1.75   |
| WDC       | WD3200AAKS-22SBA0  | 320 GB | 1       | 633   | 0     | 1.73   |
| Hitachi   | HDS723020BLE640    | 2 TB   | 6       | 632   | 0     | 1.73   |
| WDC       | WD2500AAKS-00VSA0  | 250 GB | 20      | 871   | 20    | 1.73   |
| WDC       | WD20EARS-00S8B1    | 2 TB   | 8       | 782   | 2     | 1.73   |
| WDC       | WD10EAVS-00D7B1    | 1 TB   | 5       | 809   | 2     | 1.73   |
| Hitachi   | HTS723220L9A360    | 200 GB | 1       | 630   | 0     | 1.73   |
| WDC       | WD1600AABS-00PRA0  | 160 GB | 1       | 630   | 0     | 1.73   |
| WDC       | WD1001FALS-00E3A0  | 1 TB   | 3       | 839   | 1     | 1.73   |
| WDC       | WD2002FAEX-007BA0  | 2 TB   | 15      | 921   | 3     | 1.73   |
| Seagate   | ST3160812AS        | 160 GB | 34      | 987   | 346   | 1.72   |
| WDC       | WD7500BPKX-60HPJT0 | 752 GB | 1       | 627   | 0     | 1.72   |
| WDC       | WD4000BEVT-11ZAT0  | 400 GB | 1       | 626   | 0     | 1.72   |
| WDC       | WD1600AAJB-00WRA0  | 160 GB | 2       | 950   | 543   | 1.72   |
| WDC       | WD2002FYPS-02W3B0  | 2 TB   | 1       | 626   | 0     | 1.72   |
| WDC       | WD800JD-22MSA1     | 80 GB  | 8       | 625   | 0     | 1.71   |
| WDC       | WD15EADS-00R6B0    | 1.5 TB | 1       | 625   | 0     | 1.71   |
| WDC       | WD2500AAJS-08L7A0  | 250 GB | 2       | 624   | 0     | 1.71   |
| Samsung   | HD103UJ            | 1 TB   | 35      | 938   | 167   | 1.71   |
| WDC       | WD360GD-00FLC0     | 37 GB  | 1       | 622   | 0     | 1.70   |
| WDC       | WD800AAJS-00PSA0   | 80 GB  | 13      | 759   | 57    | 1.70   |
| Hitachi   | HDS723015BLA642    | 1.5 TB | 6       | 877   | 33    | 1.70   |
| WDC       | WD1600AAJS-55PSA0  | 160 GB | 1       | 620   | 0     | 1.70   |
| WDC       | WD6400BEVT-00A0RT0 | 640 GB | 1       | 619   | 0     | 1.70   |
| Fujitsu   | MHZ2250BH G1       | 250 GB | 2       | 618   | 0     | 1.69   |
| Hitachi   | HDS5C1032CLA382    | 320 GB | 4       | 714   | 3     | 1.69   |
| Seagate   | ST9750422AS        | 752 GB | 2       | 618   | 0     | 1.69   |
| WDC       | WD5003ABYX-01WERA1 | 500 GB | 5       | 765   | 1     | 1.69   |
| WDC       | WD3200AAJS-65VWA0  | 320 GB | 2       | 617   | 0     | 1.69   |
| Seagate   | ST3320418AS        | 320 GB | 65      | 824   | 77    | 1.69   |
| Samsung   | HD083GJ            | 80 GB  | 2       | 613   | 0     | 1.68   |
| WDC       | WD800JD-00LUA0     | 80 GB  | 1       | 610   | 0     | 1.67   |
| WDC       | WD3200AAJS-00VWA0  | 320 GB | 10      | 685   | 46    | 1.67   |
| Hitachi   | HDS721075CLA332    | 752 GB | 2       | 610   | 0     | 1.67   |
| WDC       | WD2500HHTZ-04N21V0 | 250 GB | 4       | 609   | 0     | 1.67   |
| WDC       | WD2500BEKT-75PVMT0 | 250 GB | 3       | 609   | 0     | 1.67   |
| Seagate   | ST31000526SV       | 1 TB   | 3       | 769   | 343   | 1.67   |
| WDC       | WD800JD-75MSA1     | 80 GB  | 1       | 607   | 0     | 1.66   |
| WDC       | WD1002FAEX-007BA0  | 1 TB   | 2       | 709   | 1     | 1.66   |
| WDC       | WD5000AAJS-00A8B0  | 500 GB | 3       | 605   | 0     | 1.66   |
| WDC       | WD3000JS-60PDB0    | 304 GB | 2       | 603   | 0     | 1.65   |
| Seagate   | ST980411ASG        | 80 GB  | 2       | 831   | 7     | 1.65   |
| WDC       | WD1003FBYX-01Y7B0  | 1 TB   | 5       | 1238  | 4     | 1.65   |
| Hitachi   | HTS545016B9SA02    | 160 GB | 1       | 602   | 0     | 1.65   |
| WDC       | WD10EALS-00Z8A0    | 1 TB   | 21      | 919   | 70    | 1.65   |
| Seagate   | ST9200420AS        | 200 GB | 2       | 601   | 0     | 1.65   |
| WDC       | WD800JD-23LSA0     | 80 GB  | 1       | 1202  | 1     | 1.65   |
| Hitachi   | HDS728080PLAT20    | 82 GB  | 18      | 748   | 8     | 1.65   |
| WDC       | WD1600JS-23MHB0    | 160 GB | 1       | 600   | 0     | 1.64   |
| Seagate   | ST2000DL003-9VT166 | 2 TB   | 59      | 781   | 99    | 1.64   |
| Samsung   | HD103SI            | 1 TB   | 23      | 906   | 142   | 1.64   |
| Seagate   | ST3250820AS        | 250 GB | 33      | 896   | 289   | 1.64   |
| WDC       | WD10EURX-56FH1Y0   | 1 TB   | 2       | 596   | 0     | 1.63   |
| Samsung   | HD320KJ            | 320 GB | 2       | 595   | 0     | 1.63   |
| WDC       | WD1600AAJS-00PSA0  | 160 GB | 23      | 884   | 61    | 1.63   |
| WDC       | WD7501AALS-00J7B0  | 752 GB | 13      | 971   | 68    | 1.63   |
| WDC       | WD6400AAKS-65Z7B0  | 640 GB | 5       | 739   | 6     | 1.63   |
| WDC       | WD800AAJS-00WAA0   | 80 GB  | 4       | 594   | 3     | 1.63   |
| WDC       | WD10EURX-63FH1Y0   | 1 TB   | 4       | 592   | 0     | 1.62   |
| WDC       | WD5000AAKS-00D2B0  | 500 GB | 11      | 986   | 8     | 1.62   |
| Seagate   | ST3160316AS        | 160 GB | 10      | 730   | 8     | 1.62   |
| Apple     | HDD ST750LM022     | 752 GB | 1       | 589   | 0     | 1.61   |
| WDC       | WD800JD-19LSA0     | 80 GB  | 1       | 588   | 0     | 1.61   |
| Seagate   | ST1000DL002-9TT153 | 1 TB   | 25      | 976   | 363   | 1.61   |
| WDC       | WD10EZEX-00ZF5A0   | 1 TB   | 12      | 704   | 172   | 1.61   |
| WDC       | WD1600AAJS-00M0A0  | 160 GB | 6       | 784   | 68    | 1.61   |
| WDC       | WD800JD-22LSA0     | 80 GB  | 7       | 765   | 94    | 1.60   |
| WDC       | WD20EARS-55MVWB0   | 2 TB   | 1       | 584   | 0     | 1.60   |
| WDC       | WD2500AVJS-63WDA0  | 250 GB | 2       | 582   | 0     | 1.60   |
| WDC       | WD1600BEVS-75RST0  | 160 GB | 2       | 579   | 0     | 1.59   |
| Maxtor    | STM3320620A        | 320 GB | 2       | 579   | 0     | 1.59   |
| Toshiba   | MK1032GSX          | 100 GB | 4       | 579   | 0     | 1.59   |
| WDC       | WD2500BEKT-60V5T1  | 250 GB | 1       | 578   | 0     | 1.59   |
| Seagate   | ST3500630AS        | 500 GB | 25      | 937   | 320   | 1.59   |
| WDC       | WD1600BB-55RDA0    | 160 GB | 3       | 682   | 2     | 1.58   |
| WDC       | WD3200AAKS-00L9A0  | 320 GB | 36      | 877   | 13    | 1.58   |
| Seagate   | ST340014A          | 40 GB  | 73      | 784   | 40    | 1.58   |
| WDC       | WD1002FBYS-02A6B0  | 1 TB   | 4       | 747   | 2     | 1.58   |
| WDC       | WD2500BUCT-63TWBY0 | 250 GB | 2       | 884   | 519   | 1.58   |
| Samsung   | SP1644N            | 160 GB | 3       | 683   | 527   | 1.58   |
| WDC       | WD1002FAEX-00Z3A0  | 1 TB   | 43      | 770   | 121   | 1.57   |
| WDC       | WD1500ADFD-00NLR1  | 150 GB | 1       | 574   | 0     | 1.57   |
| Toshiba   | MQ01ABC150         | 1.5 TB | 1       | 574   | 0     | 1.57   |
| WDC       | WD800JD-75JNA0     | 80 GB  | 3       | 1489  | 39    | 1.57   |
| Samsung   | HD103SJ            | 1 TB   | 73      | 734   | 13    | 1.57   |
| Seagate   | ST3160212AS        | 160 GB | 2       | 572   | 0     | 1.57   |
| WDC       | WD15EARS-00S0XB0   | 1.5 TB | 2       | 912   | 1     | 1.57   |
| WDC       | WD15EVDS-63V9B1    | 1.5 TB | 1       | 571   | 0     | 1.57   |
| Seagate   | ST1000VX000-9YW162 | 1 TB   | 4       | 570   | 0     | 1.56   |
| WDC       | WD2500AAJS-07M0A0  | 250 GB | 4       | 815   | 4     | 1.56   |
| Seagate   | ST31000525SV       | 1 TB   | 2       | 938   | 2     | 1.56   |
| Hitachi   | HDS721010CLA332    | 1 TB   | 86      | 877   | 85    | 1.56   |
| WDC       | WD800JD-55MUA1     | 80 GB  | 6       | 648   | 2     | 1.55   |
| WDC       | WD6400AAKS-65A7B2  | 640 GB | 11      | 1059  | 45    | 1.54   |
| Seagate   | ST3250620AS        | 250 GB | 44      | 892   | 378   | 1.54   |
| Apple     | HDD TOSHIBA MK5... | 500 GB | 1       | 560   | 0     | 1.54   |
| Samsung   | HD253GJ            | 250 GB | 7       | 768   | 17    | 1.53   |
| WDC       | WD1000DHTZ-04N21V1 | 1 TB   | 1       | 559   | 0     | 1.53   |
| WDC       | WD2500JB-98GVA0    | 250 GB | 1       | 3354  | 5     | 1.53   |
| Fujitsu   | MHY2250BH          | 250 GB | 5       | 862   | 65    | 1.53   |
| WDC       | WD2500AAJB-00WGA0  | 250 GB | 5       | 1069  | 115   | 1.53   |
| WDC       | WD2000JS-00MHB0    | 200 GB | 7       | 769   | 20    | 1.53   |
| Seagate   | ST3160212A         | 160 GB | 9       | 802   | 90    | 1.53   |
| WDC       | WD800JD-00LSA5     | 80 GB  | 2       | 557   | 0     | 1.53   |
| Hitachi   | HDT722525DLA380    | 250 GB | 9       | 1223  | 3     | 1.52   |
| WDC       | WD3000JS-00PDB0    | 304 GB | 1       | 554   | 0     | 1.52   |
| Samsung   | HD204UI            | 2 TB   | 17      | 870   | 57    | 1.52   |
| Hitachi   | HDS721612PLA380    | 120 GB | 6       | 1022  | 3     | 1.52   |
| Seagate   | ST32000645NS       | 2 TB   | 4       | 553   | 0     | 1.52   |
| Seagate   | ST380815AS         | 80 GB  | 113     | 775   | 237   | 1.52   |
| Seagate   | ST3160815AS        | 160 GB | 138     | 790   | 400   | 1.51   |
| WDC       | WD5000AVCS-732DY1  | 500 GB | 1       | 551   | 0     | 1.51   |
| WDC       | WD3200BPVT-00HXZT0 | 320 GB | 1       | 549   | 0     | 1.51   |
| WDC       | WD1600JS-00SGB0    | 160 GB | 1       | 549   | 0     | 1.50   |
| WDC       | WD5003ABYX-01WERA0 | 500 GB | 7       | 754   | 2     | 1.50   |
| WDC       | WD400BB-00JHC0     | 40 GB  | 4       | 872   | 24    | 1.50   |
| Seagate   | ST360015A          | 64 GB  | 2       | 1494  | 5     | 1.50   |
| WDC       | WD15EARX-00PASB0   | 1.5 TB | 8       | 636   | 3     | 1.50   |
| WDC       | WD360ADFD-00NLR1   | 37 GB  | 1       | 547   | 0     | 1.50   |
| WDC       | WD3200AAKS-75L9A0  | 320 GB | 14      | 702   | 47    | 1.50   |
| Hitachi   | HDS728080PLA380    | 80 GB  | 35      | 883   | 65    | 1.50   |
| Seagate   | ST3500320NS        | 500 GB | 13      | 920   | 433   | 1.50   |
| Seagate   | ST3200827A         | 200 GB | 1       | 544   | 0     | 1.49   |
| WDC       | WD10EARX-00N0YB0   | 1 TB   | 44      | 698   | 4     | 1.49   |
| Seagate   | ST3200820AS        | 200 GB | 21      | 844   | 506   | 1.49   |
| MediaMax  | WL1000GSA6472C     | 1 TB   | 1       | 543   | 0     | 1.49   |
| Hitachi   | HDT725025VLAT80    | 250 GB | 2       | 1843  | 2     | 1.49   |
| WDC       | WD2500BEVS-26UST0  | 250 GB | 5       | 540   | 0     | 1.48   |
| WDC       | WD3000HLFS-01G6U0  | 304 GB | 1       | 540   | 0     | 1.48   |
| Seagate   | ST3000VN000-1HJ166 | 3 TB   | 1       | 540   | 0     | 1.48   |
| WDC       | WD2000JB-00REA0    | 200 GB | 3       | 837   | 1     | 1.48   |
| WDC       | WD10EADS-114BB1    | 1 TB   | 1       | 1079  | 1     | 1.48   |
| WDC       | WD1200JS-00NCB1    | 120 GB | 1       | 539   | 0     | 1.48   |
| WDC       | WD7500AZEX-00RKKA0 | 752 GB | 6       | 538   | 0     | 1.48   |
| Seagate   | ST4000NM0033-9Z... | 4 TB   | 2       | 538   | 0     | 1.47   |
| HGST      | HUH721212ALN600    | 12 TB  | 1       | 534   | 0     | 1.46   |
| WDC       | WD5002ABYS-01B1B0  | 500 GB | 9       | 915   | 3     | 1.46   |
| WDC       | WD800AAJS-22L7A0   | 80 GB  | 1       | 534   | 0     | 1.46   |
| WDC       | WD10EZEX-00ER1A0   | 1 TB   | 3       | 533   | 0     | 1.46   |
| Samsung   | HD321HJ            | 320 GB | 4       | 909   | 39    | 1.46   |
| WDC       | WD1600JS-22MHB0    | 160 GB | 3       | 700   | 9     | 1.46   |
| Hitachi   | HDT725050VLA360    | 500 GB | 4       | 1238  | 46    | 1.46   |
| WDC       | WD2500AAKX-083CA1  | 250 GB | 8       | 981   | 4     | 1.46   |
| Seagate   | ST3750640NS        | 752 GB | 6       | 1275  | 524   | 1.45   |
| WDC       | WD5000AADS-00L4B1  | 500 GB | 6       | 832   | 6     | 1.45   |
| WDC       | WD800BB-00JKC0     | 80 GB  | 1       | 527   | 0     | 1.44   |
| WDC       | WD5000AACS-00G8B1  | 500 GB | 11      | 726   | 3     | 1.44   |
| Seagate   | ST3320620A         | 320 GB | 21      | 685   | 5     | 1.44   |
| WDC       | WD7500BPVT-00HXZT1 | 752 GB | 1       | 525   | 0     | 1.44   |
| Maxtor    | 4K020H1            | 20 GB  | 1       | 522   | 0     | 1.43   |
| WDC       | WD800JD-00MSA1     | 80 GB  | 8       | 762   | 10    | 1.43   |
| WDC       | WD3200BPVT-00JJ5T0 | 320 GB | 8       | 575   | 1     | 1.42   |
| Maxtor    | STM3320820AS       | 320 GB | 12      | 793   | 89    | 1.41   |
| Fujitsu   | MHW2120BH          | 120 GB | 17      | 591   | 31    | 1.41   |
| Seagate   | ST3160215ACE       | 160 GB | 3       | 809   | 72    | 1.41   |
| Seagate   | ST5000DM000-1FK178 | 5 TB   | 4       | 520   | 2     | 1.41   |
| WDC       | WD1600BEVS-22RST0  | 160 GB | 35      | 612   | 65    | 1.41   |
| WDC       | WD10EADS-00P8B0    | 1 TB   | 4       | 846   | 4     | 1.40   |
| WDC       | WD1500HLFS-01MZUV0 | 150 GB | 2       | 511   | 0     | 1.40   |
| Seagate   | ST640LM000 HM641JI | 640 GB | 2       | 511   | 0     | 1.40   |
| WDC       | WD3200AAKS-00B3A0  | 320 GB | 32      | 727   | 35    | 1.40   |
| Seagate   | ST3120026A         | 120 GB | 19      | 881   | 161   | 1.40   |
| Seagate   | ST3000VX000-1CU166 | 3 TB   | 3       | 509   | 0     | 1.40   |
| WDC       | WD3200AAJS-55B4A0  | 320 GB | 2       | 749   | 4     | 1.40   |
| Seagate   | ST3250624AS        | 250 GB | 12      | 787   | 110   | 1.39   |
| WDC       | WD6400AAKS-55A7B0  | 640 GB | 1       | 507   | 0     | 1.39   |
| WDC       | WD20EADS-00R6B0    | 2 TB   | 5       | 766   | 3     | 1.39   |
| Seagate   | ST380011A          | 80 GB  | 139     | 785   | 92    | 1.39   |
| Samsung   | HD642JJ            | 640 GB | 17      | 1048  | 320   | 1.39   |
| Toshiba   | MK2559GSXP         | 250 GB | 3       | 506   | 0     | 1.39   |
| WDC       | WD10JMVW-11AJGS2   | 1 TB   | 2       | 558   | 4     | 1.38   |
| WDC       | WD20EARS-00MVWB0   | 2 TB   | 43      | 826   | 84    | 1.38   |
| Toshiba   | MK2556GSYF         | 250 GB | 1       | 503   | 0     | 1.38   |
| WDC       | WD1600AAJS-00B4A0  | 160 GB | 17      | 715   | 81    | 1.37   |
| Seagate   | ST3160023A         | 160 GB | 16      | 827   | 320   | 1.37   |
| WDC       | WD1600BEVS-07RST0  | 160 GB | 5       | 566   | 1     | 1.37   |
| Seagate   | ST380012ACE        | 80 GB  | 4       | 498   | 0     | 1.37   |
| Seagate   | ST320LM000 HM321HI | 320 GB | 9       | 520   | 2     | 1.36   |
| WDC       | WD400BB-00JHA0     | 40 GB  | 3       | 1145  | 4     | 1.36   |
| WDC       | WD800JD-55MSA1     | 80 GB  | 2       | 497   | 0     | 1.36   |
| Samsung   | HD502HJ            | 500 GB | 79      | 697   | 85    | 1.36   |
| WDC       | WD5000BPKT-60PK4T0 | 500 GB | 2       | 679   | 128   | 1.36   |
| WDC       | WD200EB-00BHF0     | 20 GB  | 1       | 992   | 1     | 1.36   |
| WDC       | WD4000FYYZ-01UL1B1 | 4 TB   | 2       | 496   | 0     | 1.36   |
| WDC       | WD1200JD-00GBB0    | 120 GB | 3       | 754   | 4     | 1.36   |
| Seagate   | ST3500630NS        | 500 GB | 5       | 684   | 529   | 1.36   |
| Fujitsu   | MPE3136AH          | 13 GB  | 1       | 494   | 0     | 1.35   |
| Hitachi   | HUA723020ALA641    | 2 TB   | 9       | 580   | 1     | 1.35   |
| WDC       | WD10EADX-22TDHB0   | 1 TB   | 3       | 634   | 3     | 1.35   |
| WDC       | WD5000AAKS-00V2B0  | 500 GB | 3       | 663   | 1     | 1.35   |
| WDC       | WD4000AAKS-00TMA0  | 400 GB | 4       | 561   | 1     | 1.35   |
| Samsung   | HD502IJ            | 500 GB | 25      | 918   | 299   | 1.35   |
| WDC       | WD800BB-55JKA0     | 80 GB  | 4       | 665   | 1     | 1.34   |
| HGST      | HDN726060ALE614    | 6 TB   | 2       | 490   | 0     | 1.34   |
| WDC       | WD10JPVT-16A1YT0   | 1 TB   | 1       | 490   | 0     | 1.34   |
| Seagate   | ST2000NM0033-9Z... | 2 TB   | 6       | 489   | 0     | 1.34   |
| WDC       | WD800BB-00JHA0     | 80 GB  | 8       | 827   | 4     | 1.34   |
| Hitachi   | HDS721050CLA660    | 500 GB | 13      | 543   | 7     | 1.34   |
| WDC       | WD7500AADS-00M2B0  | 752 GB | 16      | 903   | 23    | 1.34   |
| WDC       | WD740ADFD-00NLR5   | 74 GB  | 2       | 486   | 0     | 1.33   |
| Seagate   | ST98823A           | 80 GB  | 4       | 633   | 323   | 1.33   |
| Seagate   | ST9500420ASG       | 500 GB | 2       | 572   | 1     | 1.33   |
| Fujitsu   | MHT2040AH          | 40 GB  | 1       | 484   | 0     | 1.33   |
| Seagate   | ST1000VM002-1CT162 | 1 TB   | 3       | 484   | 0     | 1.33   |
| Apple     | HDD HTS545050A7... | 500 GB | 10      | 512   | 2     | 1.33   |
| WDC       | WD1200JB-00GVA0    | 120 GB | 4       | 754   | 1     | 1.32   |
| Seagate   | ST340015A          | 40 GB  | 5       | 835   | 33    | 1.32   |
| WDC       | WD5000BPKX-80HPJT0 | 500 GB | 1       | 480   | 0     | 1.32   |
| Hitachi   | HDS728040PLA320    | 40 GB  | 2       | 1225  | 8     | 1.32   |
| WDC       | WD40EZRX-00SPEB0   | 4 TB   | 6       | 661   | 6     | 1.31   |
| Seagate   | ST3750525AS        | 752 GB | 11      | 632   | 3     | 1.31   |
| WDC       | WD7502AAEX-00Y9A0  | 752 GB | 5       | 478   | 0     | 1.31   |
| WDC       | WD7500BPKX-75HPJT0 | 752 GB | 2       | 478   | 0     | 1.31   |
| WDC       | WD30EZRX-00D8PB0   | 3 TB   | 11      | 544   | 1     | 1.31   |
| WDC       | WD6400AAKS-22A7B0  | 640 GB | 8       | 905   | 4     | 1.31   |
| WDC       | WD5000AAKX-603CA0  | 500 GB | 9       | 552   | 113   | 1.31   |
| Hitachi   | HUA722050CLA330    | 500 GB | 2       | 476   | 0     | 1.31   |
| Apple     | HDD ST1000DM003    | 1 TB   | 2       | 476   | 0     | 1.31   |
| Seagate   | ST9120821A         | 120 GB | 4       | 709   | 20    | 1.30   |
| WDC       | WD20EARX-00PASB0   | 2 TB   | 58      | 759   | 144   | 1.30   |
| WDC       | WD1600JS-56MHB1    | 160 GB | 6       | 572   | 5     | 1.30   |
| WDC       | WD40EFRX-68WT0N0   | 4 TB   | 22      | 602   | 2     | 1.30   |
| WDC       | WD3200AAJB-56R1A0  | 320 GB | 1       | 473   | 0     | 1.30   |
| WDC       | WD5000AAKS-00V0A0  | 500 GB | 3       | 556   | 2     | 1.30   |
| WDC       | WD7500AZEX-00ZF5A0 | 752 GB | 6       | 472   | 0     | 1.29   |
| WDC       | WD10EACS-65D6B0    | 1 TB   | 1       | 471   | 0     | 1.29   |
| WDC       | WD5000AAKS-75A7B2  | 500 GB | 3       | 1036  | 6     | 1.29   |
| Seagate   | ST3500413AS        | 500 GB | 100     | 617   | 70    | 1.29   |
| Samsung   | HD252HJ            | 250 GB | 19      | 794   | 135   | 1.29   |
| WDC       | WD5000BEKT-75KA9T0 | 500 GB | 3       | 469   | 0     | 1.29   |
| Hitachi   | HDS721050CLA362    | 500 GB | 106     | 651   | 12    | 1.28   |
| WDC       | WD2000JB-00GVA0    | 200 GB | 2       | 468   | 0     | 1.28   |
| WDC       | WD7500BPKT-80PK4T0 | 752 GB | 2       | 467   | 0     | 1.28   |
| WDC       | WD5000AZRX-00A8LB0 | 500 GB | 61      | 487   | 1     | 1.28   |
| WDC       | WD3200AAKS-61L9A0  | 320 GB | 4       | 471   | 8     | 1.28   |
| Seagate   | ST32000646NS       | 2 TB   | 1       | 467   | 0     | 1.28   |
| Samsung   | SV0221N            | 20 GB  | 1       | 2328  | 4     | 1.28   |
| Hitachi   | HDT721010SLA360    | 1 TB   | 22      | 1069  | 18    | 1.28   |
| Hitachi   | HDT721064SLA380    | 640 GB | 1       | 464   | 0     | 1.27   |
| WDC       | WD5000AAKX-07U6AA0 | 500 GB | 1       | 464   | 0     | 1.27   |
| WDC       | WD10EARS-00Z5B1    | 1 TB   | 7       | 738   | 92    | 1.27   |
| WDC       | WD2500AAJS-00V4A0  | 250 GB | 3       | 589   | 1     | 1.27   |
| WDC       | WD1600AAJS-08PSA0  | 160 GB | 7       | 669   | 13    | 1.27   |
| Seagate   | ST3808110AS        | 80 GB  | 29      | 916   | 418   | 1.27   |
| WDC       | WD2500AAKS-00L9A0  | 250 GB | 9       | 908   | 5     | 1.27   |
| Fujitsu   | MHY2080BH          | 80 GB  | 1       | 462   | 0     | 1.27   |
| WDC       | WD30EFRX-68EUZN0   | 3 TB   | 25      | 644   | 1     | 1.26   |
| WDC       | WD1600AAJS-00V4A0  | 160 GB | 6       | 463   | 13    | 1.26   |
| Samsung   | HD105SI            | 1 TB   | 7       | 686   | 552   | 1.26   |
| WDC       | WD2500JS-22MHB0    | 250 GB | 4       | 580   | 70    | 1.26   |
| Hitachi   | HDS721616PLA380    | 160 GB | 74      | 868   | 90    | 1.26   |
| Hitachi   | HTS725050A9A362    | 500 GB | 2       | 457   | 0     | 1.25   |
| WDC       | WD2003FZEX-00SRLA0 | 2 TB   | 2       | 457   | 0     | 1.25   |
| Seagate   | ST380012A          | 80 GB  | 1       | 456   | 0     | 1.25   |
| WDC       | WD2500AABS-00SDA0  | 250 GB | 1       | 455   | 0     | 1.25   |
| Seagate   | ST2000VX003-1HH164 | 2 TB   | 2       | 454   | 0     | 1.25   |
| Toshiba   | HDWE150            | 5 TB   | 1       | 454   | 0     | 1.25   |
| Seagate   | ST3120026AS        | 120 GB | 23      | 1113  | 8     | 1.24   |
| Hitachi   | HDP725050GLA360    | 500 GB | 67      | 933   | 38    | 1.24   |
| Seagate   | ST380215AS         | 80 GB  | 19      | 865   | 707   | 1.24   |
| Hitachi   | HTS541610J9SA00    | 100 GB | 2       | 453   | 0     | 1.24   |
| WDC       | WD2003FZEX-00Z4SA0 | 2 TB   | 7       | 558   | 2     | 1.24   |
| Seagate   | ST3250620A         | 250 GB | 12      | 669   | 53    | 1.24   |
| WDC       | WD5000BEVT-75A0RT0 | 500 GB | 4       | 451   | 0     | 1.24   |
| WDC       | WD800JD-60LSA0     | 80 GB  | 5       | 715   | 158   | 1.24   |
| Samsung   | HD153WI            | 1.5 TB | 1       | 451   | 0     | 1.24   |
| WDC       | WD7500BPVT-55HXZT3 | 752 GB | 1       | 451   | 0     | 1.24   |
| WDC       | WD1600JS-00NCB1    | 160 GB | 13      | 551   | 12    | 1.23   |
| Hitachi   | HDS5C1050CLA382    | 500 GB | 11      | 664   | 124   | 1.23   |
| Hitachi   | HDS728080PLA380... | 80 GB  | 1       | 449   | 0     | 1.23   |
| Seagate   | ST1000NM0011       | 1 TB   | 6       | 705   | 45    | 1.23   |
| WDC       | WD5000BEKT-00KA9T0 | 500 GB | 2       | 1084  | 7     | 1.23   |
| ExcelStor | J360               | 61 GB  | 1       | 897   | 1     | 1.23   |
| Toshiba   | MK1234GAX          | 120 GB | 2       | 448   | 0     | 1.23   |
| Seagate   | ST380013AS         | 80 GB  | 29      | 1249  | 94    | 1.23   |
| WDC       | WD800JB-00JJA0     | 80 GB  | 2       | 873   | 8     | 1.23   |
| Hitachi   | HTS541064A9E680    | 640 GB | 3       | 447   | 0     | 1.23   |
| WDC       | WD1000CHTZ-04JCPV0 | 1 TB   | 1       | 447   | 0     | 1.23   |
| WDC       | WD15EARX-00ZUDB0   | 1.5 TB | 2       | 776   | 3     | 1.22   |
| WDC       | WD3200YS-01PGB0    | 320 GB | 1       | 446   | 0     | 1.22   |
| Seagate   | ST3200820A         | 200 GB | 5       | 491   | 61    | 1.22   |
| WDC       | WD1600AAJS-00Z4A0  | 160 GB | 1       | 445   | 0     | 1.22   |
| Seagate   | ST3200826AS        | 200 GB | 11      | 839   | 87    | 1.22   |
| WDC       | WD10EZEX-00RKKA0   | 1 TB   | 63      | 544   | 67    | 1.22   |
| WDC       | WD3200AAJS-00B4A0  | 320 GB | 15      | 875   | 142   | 1.22   |
| WDC       | WD740GD-00FLA2     | 74 GB  | 1       | 1330  | 2     | 1.22   |
| WDC       | WD2500AAKS-00VYA0  | 250 GB | 3       | 443   | 0     | 1.21   |
| WDC       | WD1600BEKT-75A25T0 | 160 GB | 1       | 442   | 0     | 1.21   |
| WDC       | WD10EARS-22Y5B1    | 1 TB   | 10      | 773   | 26    | 1.21   |
| WDC       | WD5000AAKX-221CA0  | 500 GB | 1       | 882   | 1     | 1.21   |
| WDC       | WD15EZRX-00DC0B0   | 1.5 TB | 1       | 438   | 0     | 1.20   |
| Samsung   | HD501LJ            | 500 GB | 33      | 808   | 344   | 1.20   |
| Samsung   | HD155UI            | 1.5 TB | 1       | 437   | 0     | 1.20   |
| WDC       | WD1200BEVS-22UST0  | 120 GB | 15      | 577   | 107   | 1.19   |
| WDC       | WD1600BEVT-00ZCT0  | 160 GB | 3       | 435   | 0     | 1.19   |
| Seagate   | ST3000DM001-1ER166 | 3 TB   | 16      | 435   | 0     | 1.19   |
| WDC       | WD5000AAVS-00ZTB0  | 500 GB | 3       | 434   | 0     | 1.19   |
| Seagate   | ST380817AS         | 80 GB  | 37      | 685   | 8     | 1.19   |
| WDC       | WD1600AAJS-60M0A0  | 160 GB | 3       | 527   | 31    | 1.19   |
| Seagate   | ST3160318AS        | 160 GB | 43      | 669   | 83    | 1.19   |
| WDC       | WD7500BPKX-80HPJT0 | 752 GB | 2       | 432   | 0     | 1.19   |
| Seagate   | ST1000DM005 HD1... | 1 TB   | 11      | 529   | 2     | 1.19   |
| WDC       | WD6400AAKS-00H2B0  | 640 GB | 1       | 432   | 0     | 1.19   |
| WDC       | WD1200BEVS-22RST0  | 120 GB | 3       | 458   | 1     | 1.18   |
| Hitachi   | HDP725025GLA380    | 250 GB | 30      | 830   | 89    | 1.18   |
| Hitachi   | HTS543216A7A384    | 160 GB | 2       | 430   | 0     | 1.18   |
| Hitachi   | HTE545025B9A300    | 250 GB | 1       | 430   | 0     | 1.18   |
| WDC       | WD1200JS-00MHB1    | 120 GB | 2       | 647   | 12    | 1.18   |
| WDC       | WD2500AAJS-22VTA0  | 250 GB | 8       | 603   | 4     | 1.18   |
| WDC       | WD5002AALX-00J37A0 | 500 GB | 8       | 623   | 3     | 1.17   |
| WDC       | WD1001FAES-55W7A0  | 1 TB   | 2       | 427   | 0     | 1.17   |
| Seagate   | ST3160215A         | 160 GB | 17      | 652   | 180   | 1.17   |
| WDC       | WD3200AAJS-60Z0A0  | 320 GB | 5       | 704   | 49    | 1.17   |
| WDC       | WD3200AAKS-00SBA0  | 320 GB | 9       | 687   | 21    | 1.17   |
| WDC       | WD10EARS-003BB1    | 1 TB   | 9       | 626   | 191   | 1.17   |
| WDC       | WD1200LB-55EDA0    | 120 GB | 1       | 425   | 0     | 1.17   |
| WDC       | WD5000AAKS-00WWPA0 | 500 GB | 7       | 672   | 11    | 1.16   |
| WDC       | WD6400BPVT-80HXZT3 | 640 GB | 8       | 664   | 9     | 1.16   |
| Fujitsu   | MHV2100AT PL       | 100 GB | 1       | 424   | 0     | 1.16   |
| WDC       | WD2500JS-00SGB0    | 250 GB | 5       | 570   | 1     | 1.16   |
| Seagate   | ST3250312AS        | 250 GB | 18      | 649   | 59    | 1.16   |
| Seagate   | ST3750640AS        | 752 GB | 9       | 1073  | 318   | 1.16   |
| Maxtor    | STM3160215AS       | 160 GB | 14      | 860   | 515   | 1.16   |
| WDC       | WD2500AVJS-63B6A0  | 250 GB | 2       | 456   | 4     | 1.16   |
| Seagate   | ST3320820AS        | 320 GB | 8       | 530   | 385   | 1.15   |
| WDC       | WD10EALX-009BA0    | 1 TB   | 48      | 619   | 12    | 1.15   |
| WDC       | WD10EZEX-22RKKA0   | 1 TB   | 8       | 544   | 4     | 1.15   |
| Seagate   | ST3160812A         | 160 GB | 24      | 666   | 391   | 1.15   |
| WDC       | WD5000BEVT-35A0RT0 | 500 GB | 9       | 619   | 11    | 1.15   |
| Samsung   | HD161GJ            | 160 GB | 16      | 654   | 134   | 1.15   |
| WDC       | WD7500BPVT-75A1YT0 | 752 GB | 1       | 419   | 0     | 1.15   |
| WDC       | WD1600AAJS-00WAA0  | 160 GB | 6       | 450   | 3     | 1.15   |
| WDC       | WD7500BPKT-22PK4T0 | 752 GB | 6       | 418   | 0     | 1.15   |
| Seagate   | ST3160815A         | 160 GB | 35      | 699   | 248   | 1.15   |
| WDC       | WD5000AAKS-75A7B0  | 500 GB | 1       | 417   | 0     | 1.14   |
| WDC       | WD5000AAKS-65A7B0  | 500 GB | 5       | 595   | 81    | 1.14   |
| WDC       | WD2500AAKX-001CA0  | 250 GB | 26      | 535   | 55    | 1.14   |
| WDC       | WD30EZRX-00SPEB0   | 3 TB   | 2       | 417   | 0     | 1.14   |
| Maxtor    | STM3500630AS       | 500 GB | 1       | 416   | 0     | 1.14   |
| WDC       | WD5000AAJS-22YFA0  | 500 GB | 6       | 775   | 352   | 1.14   |
| Samsung   | SP1654N            | 160 GB | 7       | 841   | 321   | 1.14   |
| WDC       | WD5000AAKS-22A7B0  | 500 GB | 12      | 981   | 6     | 1.14   |
| WDC       | WD1600JS-08MHB0    | 160 GB | 1       | 414   | 0     | 1.14   |
| Maxtor    | 6V080E0            | 81 GB  | 9       | 746   | 5     | 1.14   |
| Hitachi   | HDP725040GLA360    | 400 GB | 3       | 1056  | 5     | 1.14   |
| Seagate   | ST3500411SV        | 500 GB | 2       | 694   | 37    | 1.13   |
| Hitachi   | HDS721010CLA330    | 1 TB   | 31      | 625   | 39    | 1.13   |
| WDC       | WD2500BEVS-60UST0  | 250 GB | 8       | 630   | 253   | 1.13   |
| WDC       | WD15EADS-00P8B0    | 1.5 TB | 5       | 601   | 4     | 1.13   |
| Seagate   | ST94813AS          | 40 GB  | 2       | 412   | 0     | 1.13   |
| WDC       | WD10EALX-008EA0    | 1 TB   | 3       | 412   | 0     | 1.13   |
| WDC       | WD5000BPKX-00HPJT0 | 500 GB | 2       | 411   | 0     | 1.13   |
| Maxtor    | 6V320F0            | 320 GB | 1       | 410   | 0     | 1.13   |
| Seagate   | ST3120814A         | 120 GB | 14      | 808   | 246   | 1.12   |
| WDC       | WD7500AARS-00Y5B1  | 752 GB | 10      | 484   | 3     | 1.12   |
| Hitachi   | HUA722010CLA330    | 1 TB   | 10      | 553   | 98    | 1.12   |
| WDC       | WD5003AZEX-00K1GA0 | 500 GB | 18      | 466   | 60    | 1.12   |
| Seagate   | ST3120022A         | 120 GB | 33      | 633   | 22    | 1.12   |
| WDC       | WD10JPVT-08A1YT1   | 1 TB   | 2       | 408   | 0     | 1.12   |
| Fujitsu   | MHV2080AT PL       | 80 GB  | 2       | 408   | 0     | 1.12   |
| WDC       | WD800EB-11DJF0     | 80 GB  | 1       | 407   | 0     | 1.12   |
| WDC       | WD1600AAJS-07M0A0  | 160 GB | 2       | 866   | 1     | 1.12   |
| WDC       | WD2000JB-00KFA0    | 200 GB | 1       | 1220  | 2     | 1.11   |
| WDC       | WD2500JD-00HBB0    | 250 GB | 1       | 406   | 0     | 1.11   |
| Fujitsu   | MHV2100BH          | 100 GB | 4       | 717   | 25    | 1.11   |
| Seagate   | ST3500418AS        | 500 GB | 280     | 738   | 190   | 1.11   |
| Samsung   | HM251HI            | 250 GB | 4       | 532   | 3     | 1.11   |
| WDC       | WD10EZEX-21M2NA0   | 1 TB   | 19      | 418   | 1     | 1.11   |
| WDC       | WD10EURX-63C57Y0   | 1 TB   | 1       | 405   | 0     | 1.11   |
| Hitachi   | HDS721032CLA362    | 320 GB | 36      | 749   | 28    | 1.11   |
| WDC       | WD10EZRX-00A8LB0   | 1 TB   | 36      | 448   | 8     | 1.11   |
| Hitachi   | HTS721080G9AT00    | 80 GB  | 1       | 405   | 0     | 1.11   |
| WDC       | WD2500JS-60MHB5    | 250 GB | 2       | 1170  | 18    | 1.11   |
| Seagate   | ST3000VX000-9YW166 | 3 TB   | 1       | 405   | 0     | 1.11   |
| WDC       | WD2500AAKS-00V6A0  | 250 GB | 1       | 404   | 0     | 1.11   |
| Fujitsu   | MHZ2320BH G1       | 320 GB | 5       | 572   | 5     | 1.11   |
| WDC       | WD5000AVDS-63U7B1  | 500 GB | 4       | 470   | 3     | 1.11   |
| Fujitsu   | MHV2080AH          | 80 GB  | 2       | 402   | 0     | 1.10   |
| WDC       | WD5000AAKS-007AA0  | 500 GB | 7       | 838   | 16    | 1.10   |
| HGST      | HUS726040ALE611    | 4 TB   | 1       | 401   | 0     | 1.10   |
| WDC       | WD1200BB-00GUC0    | 120 GB | 1       | 1606  | 3     | 1.10   |
| WDC       | WD5003ABYX-23 8... | 500 GB | 2       | 668   | 2     | 1.10   |
| Hitachi   | HDS723030ALA640    | 3 TB   | 2       | 400   | 0     | 1.10   |
| Fujitsu   | MHW2080BH PL       | 80 GB  | 6       | 603   | 172   | 1.10   |
| Fujitsu   | MJA2160BH FFS G1   | 160 GB | 2       | 400   | 0     | 1.10   |
| Toshiba   | MK1031GAS          | 100 GB | 2       | 647   | 4     | 1.10   |
| WDC       | WD10EADS-11P8B2    | 1 TB   | 1       | 799   | 1     | 1.10   |
| WDC       | WD7500BPVT-24HXZT1 | 752 GB | 7       | 580   | 147   | 1.09   |
| WDC       | WD10EZEX-19ZF5A0   | 1 TB   | 1       | 399   | 0     | 1.09   |
| Samsung   | HD753LJ            | 752 GB | 24      | 927   | 249   | 1.09   |
| WDC       | WD5000BPKT-22PK4T0 | 500 GB | 2       | 398   | 0     | 1.09   |
| Seagate   | ST2000LM003 HN-... | 2 TB   | 17      | 432   | 4     | 1.09   |
| WDC       | WD2500BEVS-08VAT2  | 250 GB | 2       | 398   | 0     | 1.09   |
| WDC       | WD2500JS-57MHB1    | 250 GB | 1       | 397   | 0     | 1.09   |
| WDC       | WD800BB-00JHC0     | 80 GB  | 17      | 677   | 103   | 1.09   |
| WDC       | WD2500AAKS-00YGA0  | 250 GB | 1       | 397   | 0     | 1.09   |
| WDC       | WD1600BB-22RDA0    | 160 GB | 1       | 396   | 0     | 1.09   |
| WDC       | WD3200AAKS-00L6A0  | 320 GB | 3       | 579   | 4     | 1.09   |
| WDC       | WD10JPVX-08JC3T2   | 1 TB   | 6       | 409   | 1     | 1.08   |
| WDC       | WD10EZEX-00KUWA0   | 1 TB   | 12      | 527   | 1     | 1.08   |
| HGST      | HUS722T2TALA604    | 2 TB   | 1       | 395   | 0     | 1.08   |
| Seagate   | ST5000LM000-2AN170 | 5 TB   | 1       | 395   | 0     | 1.08   |
| WDC       | WD2001FASS-00U0B0  | 2 TB   | 1       | 1578  | 3     | 1.08   |
| WDC       | WD1200BEVS-00UST0  | 120 GB | 2       | 394   | 0     | 1.08   |
| WDC       | WD1600AAJS-00L7A0  | 160 GB | 24      | 673   | 4     | 1.08   |
| Maxtor    | 6V160E0            | 160 GB | 7       | 427   | 1     | 1.08   |
| Seagate   | ST3250318AS        | 250 GB | 86      | 724   | 117   | 1.08   |
| WDC       | WD15EARS-00S8B1    | 1.5 TB | 2       | 1078  | 4     | 1.08   |
| WDC       | WD3200AAJS-08L7A0  | 320 GB | 9       | 840   | 197   | 1.07   |
| WDC       | WD2500AAJB-00J3A0  | 250 GB | 10      | 741   | 8     | 1.07   |
| Seagate   | ST320DM000-1BC14C  | 320 GB | 15      | 511   | 15    | 1.07   |
| Fujitsu   | MHV2040AH          | 40 GB  | 4       | 749   | 5     | 1.07   |
| WDC       | WD1600AAJB-00PVA0  | 160 GB | 8       | 714   | 226   | 1.07   |
| WDC       | WD20NMVW-11AV3S0   | 2 TB   | 1       | 778   | 1     | 1.07   |
| WDC       | WD5000AAKS-22V1A0  | 500 GB | 9       | 661   | 150   | 1.07   |
| Seagate   | ST2000DM001-1CH164 | 2 TB   | 90      | 495   | 133   | 1.06   |
| Fujitsu   | MJA2250BH FFS G1   | 250 GB | 2       | 388   | 0     | 1.06   |
| Seagate   | ST3802110A         | 80 GB  | 33      | 651   | 472   | 1.06   |
| WDC       | WD3200AVVS-56L2B0  | 320 GB | 6       | 631   | 65    | 1.06   |
| Seagate   | ST31000520AS       | 1 TB   | 12      | 985   | 474   | 1.06   |
| Hitachi   | HDS721680PLAT80    | 80 GB  | 5       | 866   | 4     | 1.06   |
| WDC       | WD5000AAKX-08ANVA0 | 500 GB | 2       | 386   | 0     | 1.06   |
| WDC       | WD5000AAKS-00A7B2  | 500 GB | 24      | 814   | 16    | 1.06   |
| Seagate   | ST3250823A         | 250 GB | 5       | 888   | 527   | 1.06   |
| Seagate   | ST3160215AS        | 160 GB | 14      | 572   | 612   | 1.05   |
| Seagate   | ST3250820ACE       | 250 GB | 3       | 520   | 698   | 1.05   |
| WDC       | WD5000BEVT-00A03T0 | 500 GB | 3       | 384   | 0     | 1.05   |
| Seagate   | ST1500DL003-9VT16L | 1.5 TB | 25      | 821   | 197   | 1.05   |
| WDC       | WD2500BEVT-35A23T0 | 250 GB | 22      | 511   | 29    | 1.05   |
| WDC       | WD10EARS-00MVWB0   | 1 TB   | 26      | 829   | 38    | 1.05   |
| Seagate   | ST2000DM001-9YN164 | 2 TB   | 34      | 706   | 323   | 1.05   |
| WDC       | WD800JD-22JNA0     | 80 GB  | 1       | 383   | 0     | 1.05   |
| Seagate   | ST250DM001 HD253GJ | 250 GB | 6       | 382   | 0     | 1.05   |
| WDC       | WD3000HLHX-01JJPV0 | 304 GB | 2       | 455   | 2     | 1.05   |
| Seagate   | ST1000NM0033-9Z... | 1 TB   | 20      | 391   | 51    | 1.05   |
| Seagate   | ST1500DM003-1CH16G | 1.5 TB | 7       | 416   | 2     | 1.05   |
| WDC       | WD2000JD-22HBB0    | 200 GB | 3       | 993   | 7     | 1.04   |
| Seagate   | ST3500514NS        | 500 GB | 7       | 1229  | 128   | 1.04   |
| Seagate   | ST3250824AS        | 250 GB | 17      | 775   | 747   | 1.04   |
| WDC       | WD1600AAJS-60WAA0  | 160 GB | 2       | 517   | 506   | 1.04   |
| WDC       | WD20EARX-55PASB0   | 2 TB   | 3       | 380   | 0     | 1.04   |
| Samsung   | HD161HJ 41R0186LEN | 160 GB | 1       | 380   | 0     | 1.04   |
| Seagate   | ST340212AS         | 40 GB  | 2       | 1049  | 105   | 1.04   |
| WDC       | WD40E31X-00HY4A0   | 4 TB   | 1       | 380   | 0     | 1.04   |
| WDC       | WD5000AAKX-083CA1  | 500 GB | 4       | 448   | 183   | 1.04   |
| Seagate   | ST2000NC001-1DY164 | 2 TB   | 5       | 378   | 0     | 1.04   |
| WDC       | WD5000BEVT-24A0RT0 | 500 GB | 18      | 529   | 3     | 1.04   |
| WDC       | WD1001FALS-00E8B0  | 1 TB   | 9       | 765   | 248   | 1.03   |
| WDC       | WD2000JS-00SGB0    | 200 GB | 1       | 377   | 0     | 1.03   |
| WDC       | WD5000AADS-00S9B0  | 500 GB | 84      | 681   | 29    | 1.03   |
| WDC       | WD5000AAJS-22TKA0  | 500 GB | 1       | 376   | 0     | 1.03   |
| WDC       | WD800BEVS-08RST2   | 80 GB  | 2       | 376   | 0     | 1.03   |
| WDC       | WD10EFRX-68JCSN0   | 1 TB   | 11      | 730   | 358   | 1.03   |
| WDC       | WD800BB-75JHC0     | 80 GB  | 2       | 375   | 0     | 1.03   |
| WDC       | WD800BB-00JKA0     | 80 GB  | 1       | 374   | 0     | 1.03   |
| WDC       | WD800JB-00JJC0     | 80 GB  | 20      | 613   | 27    | 1.03   |
| WDC       | WD5000AAKS-00UU3A0 | 500 GB | 45      | 696   | 29    | 1.03   |
| Seagate   | ST3160827AS        | 160 GB | 20      | 1015  | 264   | 1.02   |
| Hitachi   | HDS721050CLA662    | 500 GB | 8       | 467   | 129   | 1.02   |
| WDC       | WD20EZRX-00DC0B0   | 2 TB   | 17      | 475   | 2     | 1.02   |
| WDC       | WD5000BPVT-80HXZT3 | 500 GB | 20      | 428   | 55    | 1.02   |
| Seagate   | ST9402112A         | 40 GB  | 1       | 1117  | 2     | 1.02   |
| Samsung   | HD154UI            | 1.5 TB | 27      | 813   | 282   | 1.02   |
| Seagate   | ST1000LM044 HN-... | 1 TB   | 2       | 559   | 404   | 1.02   |
| WDC       | WD6400BPVT-22HXZT3 | 640 GB | 4       | 372   | 0     | 1.02   |
| WDC       | WD5000BEVT-00ZAT0  | 500 GB | 2       | 371   | 0     | 1.02   |
| WDC       | WD7500BPVT-80HXZT3 | 752 GB | 9       | 445   | 2     | 1.01   |
| WDC       | WD60EFRX-68MYMN1   | 6 TB   | 6       | 469   | 3     | 1.01   |
| Maxtor    | 7V300F0            | 304 GB | 1       | 738   | 1     | 1.01   |
| WDC       | WD10EZEX-08RKKA0   | 1 TB   | 3       | 368   | 0     | 1.01   |
| WDC       | WD6400AAVS-00G9B1  | 640 GB | 1       | 367   | 0     | 1.01   |
| Hitachi   | HDP725032GLA360    | 320 GB | 12      | 840   | 132   | 1.01   |
| WDC       | WD10EFRX-68PJCN0   | 1 TB   | 22      | 438   | 1     | 1.00   |
| WDC       | WD800BB-00FJA0     | 80 GB  | 6       | 443   | 35    | 1.00   |
| WDC       | WD2500BEVS-22UST0  | 250 GB | 39      | 495   | 16    | 1.00   |
| WDC       | WD3200AAJS-22L7A0  | 320 GB | 9       | 755   | 27    | 1.00   |
| Seagate   | ST1000NC001-1DY162 | 1 TB   | 3       | 365   | 0     | 1.00   |
| Seagate   | ST3200827AS        | 200 GB | 25      | 757   | 319   | 1.00   |
| WDC       | WD7500BPVT-24HXZT3 | 752 GB | 10      | 408   | 26    | 1.00   |
| WDC       | WD20EZRX-00D8PB0   | 2 TB   | 27      | 403   | 19    | 1.00   |
| Seagate   | ST1000VX000-1CU162 | 1 TB   | 22      | 379   | 46    | 1.00   |
| Seagate   | ST500DM002-1BC142  | 500 GB | 44      | 530   | 136   | 1.00   |
| WDC       | WD3200BEVT-22ZCT0  | 320 GB | 65      | 466   | 115   | 1.00   |
| Maxtor    | STM3160815AS       | 160 GB | 26      | 678   | 245   | 0.99   |
| Seagate   | ST9640423AS        | 640 GB | 4       | 949   | 380   | 0.99   |
| Seagate   | ST3200822AS        | 200 GB | 12      | 750   | 178   | 0.99   |
| WDC       | WD3200AAKB-00WHA0  | 320 GB | 1       | 360   | 0     | 0.99   |
| WDC       | WD740GD-00FLA0     | 74 GB  | 1       | 2521  | 6     | 0.99   |
| Maxtor    | STM3160212A        | 160 GB | 2       | 817   | 1     | 0.99   |
| Samsung   | SP1613N            | 160 GB | 1       | 1079  | 2     | 0.99   |
| WDC       | WD2500BEVT-22ZCT0  | 250 GB | 25      | 450   | 81    | 0.98   |
| Seagate   | ST3120827AS        | 120 GB | 42      | 709   | 11    | 0.98   |
| Seagate   | ST3500830AS        | 500 GB | 5       | 580   | 1     | 0.98   |
| Seagate   | ST3250310NS        | 250 GB | 3       | 737   | 755   | 0.98   |
| Fujitsu   | MHW2120BJ G2       | 120 GB | 1       | 356   | 0     | 0.98   |
| WDC       | WD800BEVS-07RST0   | 80 GB  | 2       | 356   | 0     | 0.98   |
| WDC       | WD6400AARS-00Y5B1  | 640 GB | 14      | 807   | 12    | 0.97   |
| WDC       | WD20NPVX-00EA4T0   | 2 TB   | 1       | 354   | 0     | 0.97   |
| WDC       | WD3200AAJS-00M0A0  | 320 GB | 2       | 574   | 1     | 0.97   |
| Toshiba   | MK3261GSYG         | 320 GB | 1       | 354   | 0     | 0.97   |
| Seagate   | ST500VT000-1DK142  | 500 GB | 2       | 354   | 0     | 0.97   |
| WDC       | WD10EADX-00TDHB0   | 1 TB   | 4       | 762   | 17    | 0.97   |
| Hitachi   | HDT721032SLA360    | 320 GB | 18      | 881   | 13    | 0.97   |
| WDC       | WD10EZEX-60M2NA0   | 1 TB   | 11      | 451   | 144   | 0.97   |
| Hitachi   | HCP725032GLA380    | 320 GB | 2       | 1010  | 2     | 0.97   |
| WDC       | WD6400AACS-00M3B0  | 640 GB | 1       | 352   | 0     | 0.97   |
| Toshiba   | MK8032GSX          | 80 GB  | 8       | 464   | 161   | 0.96   |
| WDC       | WD10JPVT-60A1YT0   | 1 TB   | 2       | 455   | 505   | 0.96   |
| WDC       | WD5000LPVT-75G33T0 | 500 GB | 4       | 407   | 2     | 0.96   |
| Fujitsu   | MHV2120AH          | 120 GB | 2       | 482   | 3     | 0.96   |
| Seagate   | ST3250310AS        | 250 GB | 124     | 819   | 219   | 0.96   |
| WDC       | WD25EZRX-00MMMB0   | 2.5 TB | 1       | 1049  | 2     | 0.96   |
| WDC       | WD3000BLFS-08YBU0  | 304 GB | 1       | 349   | 0     | 0.96   |
| WDC       | WD6000BLHX-01V7BV0 | 600 GB | 1       | 349   | 0     | 0.96   |
| WDC       | WD10EZRX-00DC0B0   | 1 TB   | 4       | 348   | 0     | 0.96   |
| WDC       | WD5000LPVX-08V0TT6 | 500 GB | 1       | 348   | 0     | 0.95   |
| WDC       | WD5000AAKS-75V0A0  | 500 GB | 5       | 370   | 2     | 0.95   |
| WDC       | WD5000AADS-00M2B0  | 500 GB | 20      | 911   | 158   | 0.95   |
| WDC       | WD5000AAKX-001CA0  | 500 GB | 140     | 603   | 52    | 0.95   |
| WDC       | WD1600AAJS-75M0A0  | 160 GB | 2       | 346   | 0     | 0.95   |
| Toshiba   | MK6465GSXN         | 640 GB | 6       | 529   | 197   | 0.95   |
| IBM/Hi... | IC35L040AVVA07-0   | 41 GB  | 3       | 711   | 2     | 0.95   |
| WDC       | WD1600BEVS-08RST2  | 160 GB | 1       | 345   | 0     | 0.95   |
| WDC       | WD6400BPVT-16HXZT1 | 640 GB | 1       | 1037  | 2     | 0.95   |
| WDC       | WD1600JS-00MHB0    | 160 GB | 6       | 658   | 31    | 0.95   |
| WDC       | WD5000BPVT-22HXZT3 | 500 GB | 34      | 452   | 32    | 0.95   |
| WDC       | WD5000BUCT-63LS5Y1 | 500 GB | 1       | 345   | 0     | 0.95   |
| WDC       | WD5000BMVW-11S5XS0 | 500 GB | 3       | 344   | 0     | 0.94   |
| WDC       | WD10EZEX-07WN4A0   | 1 TB   | 2       | 344   | 0     | 0.94   |
| WDC       | WD7500BPKT-00PK4T0 | 752 GB | 2       | 343   | 0     | 0.94   |
| WDC       | WD3200AAKS-00UU3A0 | 320 GB | 8       | 701   | 16    | 0.94   |
| Seagate   | ST500DM005 HD502HJ | 500 GB | 30      | 438   | 12    | 0.94   |
| WDC       | WD3200BPVT-55JJ5T0 | 320 GB | 5       | 395   | 195   | 0.94   |
| Samsung   | HD251HJ            | 250 GB | 7       | 753   | 62    | 0.94   |
| Seagate   | ST380811AS         | 80 GB  | 51      | 570   | 549   | 0.94   |
| Seagate   | ST3160811AS        | 160 GB | 76      | 787   | 447   | 0.94   |
| WDC       | WD6400BPVT-55HXZT2 | 640 GB | 1       | 340   | 0     | 0.93   |
| WDC       | WD10EARS-00Y5B1    | 1 TB   | 77      | 812   | 82    | 0.93   |
| WDC       | WD15EARX-22PASB0   | 1.5 TB | 1       | 340   | 0     | 0.93   |
| WDC       | WD10EALX-559BA0    | 1 TB   | 4       | 600   | 8     | 0.93   |
| Seagate   | ST3250820A         | 250 GB | 10      | 874   | 535   | 0.93   |
| WDC       | WD5000BPVT-08HXZT3 | 500 GB | 7       | 369   | 1     | 0.93   |
| Fujitsu   | MHW2160BH PL       | 160 GB | 7       | 623   | 8     | 0.93   |
| Fujitsu   | MHY2200BH          | 200 GB | 14      | 576   | 42    | 0.93   |
| WDC       | WD800JD-32LSA0     | 80 GB  | 2       | 1577  | 53    | 0.93   |
| Toshiba   | MQ03UBB200         | 2 TB   | 2       | 339   | 0     | 0.93   |
| WDC       | WD6400AAKS-22A7B2  | 640 GB | 13      | 577   | 2     | 0.93   |
| WDC       | WD10JPVT-24A1YT0   | 1 TB   | 2       | 338   | 0     | 0.93   |
| Samsung   | HD080HJ            | 80 GB  | 83      | 781   | 351   | 0.93   |
| WDC       | WD3200BPVT-35ZEST0 | 320 GB | 21      | 442   | 2     | 0.93   |
| WDC       | WD5000AAKX-00ERMA0 | 500 GB | 80      | 478   | 5     | 0.93   |
| ExcelStor | J680               | 82 GB  | 1       | 1687  | 4     | 0.92   |
| IBM/Hi... | IC35L090AVV207-0   | 80 GB  | 2       | 735   | 2     | 0.92   |
| WDC       | WD1200BEVS-75UST0  | 120 GB | 9       | 428   | 2     | 0.92   |
| WDC       | WD2500BEVS-75UST0  | 250 GB | 7       | 336   | 0     | 0.92   |
| Seagate   | ST2000VX000-1ES164 | 2 TB   | 5       | 336   | 0     | 0.92   |
| WDC       | WD20EFRX-68EUZN0   | 2 TB   | 22      | 373   | 1     | 0.92   |
| WDC       | WD20EURX-63T0FY0   | 2 TB   | 5       | 336   | 0     | 0.92   |
| HGST      | HUS724020ALA640    | 2 TB   | 6       | 335   | 0     | 0.92   |
| Samsung   | HD322HJ            | 320 GB | 20      | 627   | 92    | 0.92   |
| WDC       | WD3200BEVT-75A23T0 | 320 GB | 2       | 367   | 1     | 0.92   |
| WDC       | WD5000BHTZ-04JCPV0 | 500 GB | 1       | 334   | 0     | 0.92   |
| WDC       | WD5000BEVT-60A0RT0 | 500 GB | 1       | 667   | 1     | 0.91   |
| WDC       | WD6002FRYZ-01WD5B0 | 6 TB   | 1       | 332   | 0     | 0.91   |
| Maxtor    | STM380215AS        | 80 GB  | 8       | 566   | 614   | 0.91   |
| Seagate   | ST3250410AS        | 250 GB | 145     | 807   | 271   | 0.91   |
| Seagate   | ST9250410AS        | 250 GB | 32      | 479   | 185   | 0.91   |
| WDC       | WD1001FALS-00U9B0  | 1 TB   | 1       | 995   | 2     | 0.91   |
| Seagate   | ST1000DX001-1NS162 | 1 TB   | 4       | 375   | 3     | 0.91   |
| WDC       | WD2500AAKX-00U6AA0 | 250 GB | 3       | 334   | 3     | 0.91   |
| WDC       | WD20EARS-00J99B0   | 2 TB   | 2       | 331   | 0     | 0.91   |
| Fujitsu   | MHW2080BH          | 80 GB  | 3       | 565   | 6     | 0.90   |
| Fujitsu   | MHZ2160BH G2       | 160 GB | 21      | 521   | 362   | 0.90   |
| Toshiba   | MK6459GSXP         | 640 GB | 8       | 421   | 373   | 0.90   |
| WDC       | WD3200AAKS-00V1A0  | 320 GB | 6       | 852   | 267   | 0.90   |
| Hitachi   | HDT721075SLA360    | 752 GB | 1       | 328   | 0     | 0.90   |
| WDC       | WD6400AACS-00G8B1  | 640 GB | 5       | 715   | 6     | 0.90   |
| WDC       | WD3200LPVX-80V0TT0 | 320 GB | 2       | 328   | 0     | 0.90   |
| Seagate   | ST32000542AS       | 2 TB   | 18      | 824   | 435   | 0.90   |
| WDC       | WD5003AZEX-00MK2A0 | 500 GB | 9       | 369   | 1     | 0.90   |
| WDC       | WD2500BEVT-75ZCT2  | 250 GB | 2       | 327   | 0     | 0.90   |
| WDC       | WD10EZEX-60ZF5A0   | 1 TB   | 36      | 436   | 77    | 0.90   |
| WDC       | WD2500AAJS-00Z0A0  | 250 GB | 3       | 819   | 4     | 0.90   |
| Seagate   | ST2000VN000-1HJ164 | 2 TB   | 2       | 326   | 0     | 0.90   |
| WDC       | WD5000AAJS-19A8B0  | 500 GB | 1       | 326   | 0     | 0.90   |
| WDC       | WD6400AAKS-40H2B0  | 640 GB | 2       | 1447  | 406   | 0.90   |
| Hitachi   | HDS721010CLA630    | 1 TB   | 6       | 407   | 1     | 0.89   |
| WDC       | WD5000LPLX-66ZNTT0 | 500 GB | 1       | 326   | 0     | 0.89   |
| Toshiba   | DT01ACA300         | 3 TB   | 34      | 375   | 61    | 0.89   |
| WDC       | WD800BB-60JKA0     | 80 GB  | 1       | 325   | 0     | 0.89   |
| WDC       | WD5000BPVT-24HXZT3 | 500 GB | 15      | 384   | 1     | 0.89   |
| WDC       | WD3200AAKS-75VYA0  | 320 GB | 2       | 324   | 0     | 0.89   |
| WDC       | WD3200AAJS-00YZCA0 | 320 GB | 13      | 549   | 5     | 0.89   |
| WDC       | WD3200JS-00PDB0    | 320 GB | 1       | 324   | 0     | 0.89   |
| Samsung   | HD403LJ            | 400 GB | 14      | 1119  | 516   | 0.89   |
| WDC       | WD2500JS-58NCB1    | 250 GB | 2       | 773   | 308   | 0.89   |
| Seagate   | ST1000DM003-1CH162 | 1 TB   | 234     | 425   | 39    | 0.88   |
| Seagate   | ST31000524NS       | 1 TB   | 3       | 767   | 506   | 0.88   |
| Seagate   | ST2000VN000-1H3164 | 2 TB   | 1       | 321   | 0     | 0.88   |
| WDC       | WD800BEVT-22ZCT0   | 80 GB  | 1       | 321   | 0     | 0.88   |
| WDC       | WD3001FAEX-00MJRA0 | 3 TB   | 2       | 321   | 0     | 0.88   |
| WDC       | WD2500AAJS-08B4A0  | 250 GB | 2       | 931   | 1211  | 0.88   |
| WDC       | WD10JPVT-55A1YT0   | 1 TB   | 1       | 320   | 0     | 0.88   |
| WDC       | WD7500BPVT-26HXZT3 | 752 GB | 1       | 1277  | 3     | 0.88   |
| Toshiba   | DT01ACA200         | 2 TB   | 67      | 343   | 61    | 0.87   |
| WDC       | WD15EARS-00MVWB0   | 1.5 TB | 29      | 805   | 342   | 0.87   |
| Seagate   | ST380215A          | 80 GB  | 24      | 467   | 123   | 0.87   |
| Hitachi   | HDS721025CLA382    | 250 GB | 13      | 484   | 314   | 0.87   |
| WDC       | WD3200AAJS-61B4A0  | 320 GB | 2       | 431   | 4     | 0.87   |
| WDC       | WD5000AAKS-60Z1A0  | 500 GB | 3       | 482   | 2     | 0.87   |
| Samsung   | HD752LJ            | 752 GB | 2       | 1517  | 4     | 0.87   |
| Fujitsu   | MHV2100AT          | 100 GB | 1       | 316   | 0     | 0.87   |
| WDC       | WD5002ABYS-02B1B0  | 500 GB | 6       | 731   | 3     | 0.87   |
| WDC       | WD800BEVS-00UST0   | 80 GB  | 1       | 315   | 0     | 0.86   |
| WDC       | WD6400BEVT-60A0RT0 | 640 GB | 2       | 382   | 18    | 0.86   |
| WDC       | WD1600BEVT-22ZCT0  | 160 GB | 69      | 444   | 72    | 0.86   |
| WDC       | WD2500BEVT-00A23T0 | 250 GB | 6       | 657   | 6     | 0.86   |
| WDC       | WD2000JS-55MHB0    | 200 GB | 1       | 313   | 0     | 0.86   |
| WDC       | WD5000BPVT-22HXZT1 | 500 GB | 15      | 463   | 2     | 0.86   |
| WDC       | WD5000BPKT-00PK4T0 | 500 GB | 3       | 340   | 1     | 0.86   |
| WDC       | WD800AAJS-00L7A0   | 80 GB  | 1       | 313   | 0     | 0.86   |
| Maxtor    | STM3250820A        | 250 GB | 4       | 588   | 326   | 0.86   |
| Seagate   | ST750LX003-1AC154  | 752 GB | 10      | 371   | 106   | 0.85   |
| WDC       | WD3200BPVT-75JJ5T0 | 320 GB | 3       | 386   | 3     | 0.85   |
| Hitachi   | HDS721680PLA380    | 80 GB  | 37      | 683   | 170   | 0.85   |
| IBM/Hi... | IC35L120AVV207-0   | 128 GB | 1       | 933   | 2     | 0.85   |
| Seagate   | ST2000VX002-1AH166 | 2 TB   | 1       | 311   | 0     | 0.85   |
| WDC       | WD10EAVS-00D7B0    | 1 TB   | 1       | 309   | 0     | 0.85   |
| WDC       | WD800BB-56JKC0     | 80 GB  | 3       | 634   | 4     | 0.85   |
| Hitachi   | HTS721080G9SA00    | 80 GB  | 3       | 405   | 2     | 0.85   |
| WDC       | WD1200JB-00DUA3    | 120 GB | 1       | 1235  | 3     | 0.85   |
| WDC       | WD1600JS-40TGB0    | 160 GB | 1       | 308   | 0     | 0.85   |
| Samsung   | SP0812N            | 80 GB  | 6       | 607   | 4     | 0.85   |
| MediaMax  | WL5000GSA12872B    | 5 TB   | 1       | 308   | 0     | 0.85   |
| WDC       | WD5000LPVT-22G33T0 | 500 GB | 17      | 429   | 77    | 0.85   |
| WDC       | WD7500BPVT-22HXZT3 | 752 GB | 21      | 369   | 1     | 0.84   |
| WDC       | WD5000AAKX-00U6AA0 | 500 GB | 15      | 399   | 3     | 0.84   |
| WDC       | WD3200BEVT-00SCST0 | 320 GB | 1       | 306   | 0     | 0.84   |
| Seagate   | ST9320328CS        | 320 GB | 5       | 656   | 342   | 0.84   |
| Samsung   | HD400LJ            | 400 GB | 2       | 480   | 5     | 0.84   |
| Hitachi   | HDS721050CLA360    | 500 GB | 49      | 494   | 49    | 0.84   |
| Seagate   | ST31000524AS       | 1 TB   | 144     | 564   | 225   | 0.84   |
| Hitachi   | HTS545050B9A300    | 500 GB | 81      | 563   | 176   | 0.83   |
| WDC       | WD2500BEKT-60PVMT0 | 250 GB | 7       | 321   | 144   | 0.83   |
| Samsung   | HD502HI            | 500 GB | 17      | 526   | 98    | 0.83   |
| Samsung   | HD503HI            | 500 GB | 14      | 554   | 19    | 0.83   |
| Samsung   | HM100UI            | 1 TB   | 2       | 303   | 0     | 0.83   |
| Toshiba   | MK1234GSX          | 120 GB | 7       | 600   | 5     | 0.83   |
| Seagate   | ST250DM000-1BC141  | 250 GB | 7       | 389   | 14    | 0.83   |
| WDC       | WD3200BEVT-80A0RT0 | 320 GB | 31      | 461   | 6     | 0.83   |
| Seagate   | ST1500LM006 HN-... | 1.5 TB | 1       | 302   | 0     | 0.83   |
| Samsung   | HD321KJ            | 320 GB | 51      | 740   | 292   | 0.83   |
| Maxtor    | 6V200E0            | 208 GB | 5       | 627   | 180   | 0.83   |
| Seagate   | ST1000DM003-9YN162 | 1 TB   | 83      | 518   | 293   | 0.83   |
| WDC       | WD3200AAKX-001CA0  | 320 GB | 26      | 589   | 16    | 0.83   |
| Samsung   | HD103UI            | 1 TB   | 2       | 483   | 9     | 0.83   |
| WDC       | WD3200BEKT-60PVMT0 | 320 GB | 3       | 301   | 0     | 0.83   |
| Seagate   | ST1000DM003-1ER162 | 1 TB   | 129     | 301   | 2     | 0.83   |
| Samsung   | HM120JC            | 120 GB | 2       | 600   | 51    | 0.82   |
| Seagate   | ST320011A          | 20 GB  | 6       | 555   | 5     | 0.82   |
| WDC       | WD1600AAJS-22L7A0  | 160 GB | 14      | 542   | 51    | 0.82   |
| WDC       | WD600BEAS-22KZT0   | 64 GB  | 1       | 300   | 0     | 0.82   |
| Samsung   | HM641JI            | 640 GB | 17      | 484   | 63    | 0.82   |
| WDC       | WD10EZEX-00BN5A0   | 1 TB   | 85      | 328   | 2     | 0.82   |
| WDC       | WD30PURX-64P6ZY0   | 3 TB   | 2       | 297   | 0     | 0.82   |
| Fujitsu   | MHX2300BT          | 304 GB | 3       | 759   | 47    | 0.81   |
| Seagate   | ST940210AS         | 40 GB  | 1       | 591   | 1     | 0.81   |
| Maxtor    | STM3250620A        | 250 GB | 1       | 295   | 0     | 0.81   |
| Seagate   | ST31000528AS       | 1 TB   | 142     | 646   | 225   | 0.81   |
| WDC       | WD800JD-22JNC0     | 80 GB  | 2       | 412   | 3     | 0.81   |
| Seagate   | ST3320820SCE       | 320 GB | 1       | 294   | 0     | 0.81   |
| WDC       | WD5000AAKS-22A7B2  | 500 GB | 5       | 981   | 65    | 0.81   |
| WDC       | WD20EURS-63S48Y0   | 2 TB   | 3       | 471   | 677   | 0.81   |
| Seagate   | ST3160211AS        | 160 GB | 8       | 743   | 1099  | 0.80   |
| WDC       | WD1003FZEX-00MK2A0 | 1 TB   | 39      | 321   | 1     | 0.80   |
| WDC       | WD2503ABYX-01WERA1 | 256 GB | 3       | 515   | 1     | 0.80   |
| Samsung   | SV1203N            | 120 GB | 2       | 441   | 3     | 0.80   |
| Seagate   | ST9640320AS        | 640 GB | 8       | 489   | 255   | 0.80   |
| Seagate   | ST4000LM024-2AN17V | 4 TB   | 1       | 292   | 0     | 0.80   |
| Maxtor    | STM3160211AS       | 160 GB | 3       | 624   | 349   | 0.80   |
| WDC       | WD2500AAJS-60Z0A0  | 250 GB | 2       | 291   | 0     | 0.80   |
| WDC       | WD2500AAKX-00ERMA0 | 250 GB | 19      | 377   | 72    | 0.80   |
| WDC       | WD3200AAJS-22B4A0  | 320 GB | 4       | 1078  | 7     | 0.80   |
| WDC       | WD1003FBYZ-010FB0  | 1 TB   | 7       | 430   | 2     | 0.80   |
| Seagate   | ST4000DM000-2AE166 | 4 TB   | 1       | 291   | 0     | 0.80   |
| Magnet... | MD02500-BJDW-RO    | 250 GB | 1       | 291   | 0     | 0.80   |
| WDC       | WD1600AAJS-60M0A1  | 160 GB | 2       | 779   | 11    | 0.80   |
| Hitachi   | HCS5C1025CLA382    | 250 GB | 1       | 290   | 0     | 0.80   |
| Seagate   | OOS2000G           | 2 TB   | 1       | 289   | 0     | 0.79   |
| Samsung   | HM321HI            | 320 GB | 70      | 452   | 91    | 0.79   |
| WDC       | WD5000AZRX-00L4HB0 | 500 GB | 14      | 288   | 0     | 0.79   |
| IBM/Hi... | IC35L120AVV207-1   | 128 GB | 1       | 288   | 0     | 0.79   |
| Hitachi   | HDT725032VLA360    | 320 GB | 13      | 651   | 146   | 0.79   |
| WDC       | WD7500BPKT-75PK4T0 | 752 GB | 8       | 333   | 1     | 0.79   |
| WDC       | WD3200LPVT-08G33T1 | 320 GB | 2       | 287   | 0     | 0.79   |
| WDC       | WD3000GLFS-01F8U0  | 304 GB | 1       | 287   | 0     | 0.79   |
| WDC       | WD2500AAKS-00B3A0  | 250 GB | 4       | 710   | 8     | 0.79   |
| Maxtor    | STM380811AS        | 80 GB  | 4       | 500   | 5     | 0.79   |
| Toshiba   | MK3029GAC          | 32 GB  | 1       | 287   | 0     | 0.79   |
| WDC       | WD5000BPKX-60HPJT0 | 500 GB | 3       | 286   | 0     | 0.79   |
| WDC       | WD1200BEVT-22ZCT0  | 120 GB | 1       | 286   | 0     | 0.79   |
| WDC       | WD5000AZLX-00JKKA0 | 500 GB | 3       | 286   | 0     | 0.78   |
| WDC       | WD1200BEVS-75RST0  | 120 GB | 3       | 286   | 0     | 0.78   |
| WDC       | WD10EZRX-00L4HB0   | 1 TB   | 35      | 309   | 5     | 0.78   |
| Toshiba   | MK4025GAS          | 40 GB  | 1       | 571   | 1     | 0.78   |
| WDC       | WD800BB-00FRA0     | 80 GB  | 3       | 697   | 13    | 0.78   |
| WDC       | WD3200BPVT-22ZEST0 | 320 GB | 42      | 424   | 38    | 0.78   |
| Toshiba   | HDWA130            | 3 TB   | 1       | 285   | 0     | 0.78   |
| WDC       | WD2500BEKT-00PVMT0 | 250 GB | 1       | 284   | 0     | 0.78   |
| WDC       | WD6402AAEX-00Y9A0  | 640 GB | 2       | 555   | 15    | 0.78   |
| HP        | MB2000GCWLT        | 2 TB   | 1       | 1419  | 4     | 0.78   |
| Toshiba   | MK4058GSX          | 400 GB | 3       | 452   | 3     | 0.78   |
| Seagate   | ST320014A          | 20 GB  | 5       | 629   | 16    | 0.78   |
| WDC       | WD3200BPVT-24JJ5T0 | 320 GB | 48      | 345   | 60    | 0.78   |
| Hitachi   | HDS721032CLA662    | 320 GB | 1       | 283   | 0     | 0.78   |
| Fujitsu   | MHV2080BH          | 80 GB  | 2       | 457   | 4     | 0.77   |
| Samsung   | HN-M500MBB         | 500 GB | 27      | 410   | 4     | 0.77   |
| WDC       | WD5000AAKX-221CA1  | 500 GB | 9       | 561   | 30    | 0.77   |
| Seagate   | ST3160023AS        | 160 GB | 10      | 695   | 47    | 0.77   |
| Seagate   | ST2000DM001-1ER164 | 2 TB   | 39      | 280   | 0     | 0.77   |
| WDC       | WD10JPVT-08A1YT2   | 1 TB   | 8       | 411   | 2     | 0.77   |
| WDC       | WD7500BPVX-22JC3T0 | 752 GB | 12      | 332   | 1     | 0.77   |
| Toshiba   | MK6461GSY          | 640 GB | 3       | 281   | 13    | 0.77   |
| WDC       | WD1600JS-60NCB1    | 160 GB | 4       | 602   | 78    | 0.76   |
| Fujitsu   | MHW2100BH          | 100 GB | 1       | 279   | 0     | 0.76   |
| WDC       | WD100EB-00BHF0     | 10 GB  | 1       | 557   | 1     | 0.76   |
| WDC       | WD1600AAJS-60B4A0  | 160 GB | 2       | 602   | 10    | 0.76   |
| WDC       | WD5000AAKX-753CA1  | 500 GB | 4       | 684   | 16    | 0.76   |
| Hitachi   | HDP725050GLAT80    | 500 GB | 1       | 278   | 0     | 0.76   |
| WDC       | WD1600JD-22HBB0    | 160 GB | 1       | 1659  | 5     | 0.76   |
| Seagate   | STM3500418AS       | 500 GB | 18      | 805   | 420   | 0.76   |
| WDC       | WD2000JD-00HBB0    | 200 GB | 4       | 718   | 4     | 0.75   |
| Hitachi   | HTS545032B9A300    | 320 GB | 81      | 466   | 126   | 0.75   |
| Seagate   | STM3320418AS       | 320 GB | 10      | 644   | 140   | 0.75   |
| Seagate   | ST3000DM001-1CH166 | 3 TB   | 17      | 387   | 252   | 0.75   |
| WDC       | WD3200BEVT-60ZCT1  | 320 GB | 4       | 377   | 6     | 0.75   |
| Seagate   | ST340016A          | 40 GB  | 25      | 567   | 29    | 0.75   |
| Toshiba   | MQ01UBD100         | 1 TB   | 3       | 274   | 0     | 0.75   |
| WDC       | WD3200AAKX-00ERMA0 | 320 GB | 8       | 310   | 3     | 0.75   |
| WDC       | WD1600AABS-62PRA0  | 160 GB | 1       | 273   | 0     | 0.75   |
| WDC       | WD1600AAJS-00YZCA0 | 160 GB | 10      | 489   | 36    | 0.75   |
| WDC       | WD3200AZRX-00A8LB0 | 320 GB | 3       | 273   | 0     | 0.75   |
| Hitachi   | HUA721010KLA330    | 1 TB   | 2       | 272   | 0     | 0.75   |
| WDC       | WD10EZEX-08M2NA0   | 1 TB   | 49      | 305   | 7     | 0.75   |
| WDC       | WD3200BPVT-55ZEST0 | 320 GB | 2       | 316   | 2     | 0.75   |
| WDC       | WD7500BPVT-60HXZT3 | 752 GB | 7       | 558   | 153   | 0.75   |
| WDC       | WD2500AAJS-55M0A0  | 250 GB | 2       | 392   | 4     | 0.75   |
| WDC       | WD3200BPVT-22JJ5T0 | 320 GB | 96      | 330   | 50    | 0.74   |
| Seagate   | ST1000DX001-1CM162 | 1 TB   | 22      | 360   | 63    | 0.74   |
| WDC       | WD1200BEVS-07RST0  | 120 GB | 2       | 268   | 0     | 0.74   |
| WDC       | WD5000BPVT-00HXZT3 | 500 GB | 8       | 372   | 61    | 0.74   |
| Toshiba   | MQ01ABD075         | 752 GB | 73      | 336   | 8     | 0.73   |
| WDC       | WD5000M22K-24Z1... | 500 GB | 1       | 267   | 0     | 0.73   |
| WDC       | WD5000AAKX-08ERMA0 | 500 GB | 17      | 468   | 141   | 0.73   |
| WDC       | WD1200JD-22HBB0    | 120 GB | 2       | 1602  | 5     | 0.73   |
| WDC       | WD5000LPVT-00FMCT0 | 500 GB | 5       | 275   | 1     | 0.73   |
| WDC       | WD3200LPVT-00FMCT0 | 320 GB | 1       | 266   | 0     | 0.73   |
| WDC       | WD3200BEKX-75B7WT0 | 320 GB | 1       | 266   | 0     | 0.73   |
| Hitachi   | HTS543225L9A300    | 250 GB | 20      | 682   | 282   | 0.73   |
| WDC       | WD6000HLHX-01JJPV0 | 600 GB | 6       | 482   | 5     | 0.73   |
| Seagate   | ST9160411ASG       | 160 GB | 2       | 676   | 4     | 0.73   |
| WDC       | WD5000AAKS-65A7B2  | 500 GB | 1       | 265   | 0     | 0.73   |
| WDC       | WD10EZEX-22BN5A0   | 1 TB   | 11      | 347   | 2     | 0.73   |
| WDC       | WD2500AAKS-61L9A0  | 250 GB | 1       | 265   | 0     | 0.73   |
| WDC       | WD2500BEKT-00A25T0 | 250 GB | 1       | 264   | 0     | 0.73   |
| Toshiba   | MK5075GSX          | 500 GB | 10      | 378   | 238   | 0.72   |
| WDC       | WD2500BEKX-00B7WT0 | 250 GB | 2       | 263   | 0     | 0.72   |
| Seagate   | ST2000DX001-1NS164 | 2 TB   | 3       | 263   | 0     | 0.72   |
| Maxtor    | 6L040J2            | 40 GB  | 1       | 1576  | 5     | 0.72   |
| WDC       | WD3200AAJS-00L7A0  | 320 GB | 55      | 682   | 64    | 0.72   |
| Seagate   | ST3160021A         | 160 GB | 9       | 508   | 677   | 0.72   |
| Seagate   | ST750LM022 HN-M... | 752 GB | 77      | 350   | 31    | 0.72   |
| WDC       | WD5000AAKS-00V1A0  | 500 GB | 43      | 756   | 241   | 0.72   |
| Apple     | HDD HTS541010A9... | 1 TB   | 11      | 294   | 184   | 0.72   |
| WDC       | WD2500JB-00REA0    | 250 GB | 8       | 705   | 27    | 0.72   |
| WDC       | WD2500AAJS-00B4A0  | 250 GB | 15      | 688   | 67    | 0.72   |
| HGST      | HCC545050A7E380    | 500 GB | 1       | 523   | 1     | 0.72   |
| WDC       | WD1600BEVS-60RST0  | 160 GB | 9       | 507   | 254   | 0.72   |
| WDC       | WD6401AALS-00E3A0  | 640 GB | 4       | 602   | 5     | 0.71   |
| Hitachi   | HTS545025B9A300    | 250 GB | 88      | 498   | 141   | 0.71   |
| WDC       | WD1000DHTZ-04N21V0 | 1 TB   | 2       | 825   | 4     | 0.71   |
| Hitachi   | HTS542516K9A300    | 160 GB | 6       | 790   | 220   | 0.71   |
| WDC       | WD1600JS-60MHB5    | 160 GB | 3       | 862   | 30    | 0.71   |
| Seagate   | ST500DM002-1BD142  | 500 GB | 382     | 424   | 100   | 0.71   |
| Seagate   | ST330013A          | 32 GB  | 1       | 259   | 0     | 0.71   |
| Seagate   | ST91208220AS       | 120 GB | 2       | 461   | 507   | 0.71   |
| HGST      | HTS545032A7E680    | 320 GB | 14      | 309   | 21    | 0.71   |
| Samsung   | HD160JJ            | 160 GB | 59      | 839   | 457   | 0.71   |
| Seagate   | ST250DM000-1BD141  | 250 GB | 66      | 402   | 121   | 0.71   |
| Toshiba   | DT01ACA100         | 1 TB   | 179     | 290   | 12    | 0.71   |
| Hitachi   | HDT721032SLA380    | 320 GB | 5       | 581   | 468   | 0.70   |
| Samsung   | HM500JI            | 500 GB | 19      | 450   | 4     | 0.70   |
| WDC       | WD10EZRX-00D8PB0   | 1 TB   | 9       | 361   | 2     | 0.70   |
| WDC       | WD5000BPVT-35HXZT1 | 500 GB | 4       | 256   | 0     | 0.70   |
| WDC       | WD2500BEVT-24A23T0 | 250 GB | 19      | 371   | 33    | 0.70   |
| WDC       | WD10JPVX-08JC3T5   | 1 TB   | 4       | 254   | 0     | 0.70   |
| Fujitsu   | MHX2250BT          | 250 GB | 2       | 409   | 5     | 0.70   |
| Hitachi   | HTS545032B9SA02    | 320 GB | 2       | 840   | 30    | 0.70   |
| Maxtor    | STM3320620AS       | 320 GB | 2       | 254   | 0     | 0.70   |
| Toshiba   | DT01ABA200         | 2 TB   | 2       | 254   | 0     | 0.70   |
| Maxtor    | STM3250310AS       | 250 GB | 53      | 715   | 380   | 0.70   |
| WDC       | WD3200BPVT-80JJ5T0 | 320 GB | 50      | 327   | 47    | 0.70   |
| WDC       | WD800BB-22JHC0     | 80 GB  | 7       | 459   | 53    | 0.70   |
| WDC       | WD3200BEKT-00F3T0  | 320 GB | 2       | 253   | 0     | 0.69   |
| WDC       | WD5000AAKS-22YGA0  | 500 GB | 3       | 748   | 153   | 0.69   |
| Toshiba   | MD04ACA400         | 4 TB   | 1       | 253   | 0     | 0.69   |
| WDC       | WD40PURX-64GVNY0   | 4 TB   | 1       | 253   | 0     | 0.69   |
| Seagate   | ST320DM000-1BD14C  | 320 GB | 31      | 392   | 76    | 0.69   |
| Fujitsu   | MHY2120BH          | 120 GB | 17      | 473   | 327   | 0.69   |
| WDC       | WD7500AZEX-00BN5A0 | 752 GB | 1       | 252   | 0     | 0.69   |
| Hitachi   | HTS547575A9E384    | 640 GB | 83      | 433   | 439   | 0.69   |
| WDC       | WD5000BPVT-00HXZT1 | 500 GB | 14      | 390   | 119   | 0.69   |
| WDC       | WD5000AAKS-07A7B0  | 500 GB | 3       | 754   | 6     | 0.69   |
| Samsung   | HD250HJ            | 250 GB | 30      | 778   | 649   | 0.69   |
| WDC       | WD1600JS-08NCB1    | 160 GB | 3       | 556   | 44    | 0.69   |
| Seagate   | ST3120211AS        | 120 GB | 4       | 619   | 15    | 0.69   |
| WDC       | WD3200AAKS-00V6A0  | 320 GB | 2       | 383   | 1     | 0.69   |
| Samsung   | HD163GJ            | 160 GB | 1       | 251   | 0     | 0.69   |
| Hitachi   | HDS721010CLA632    | 1 TB   | 1       | 251   | 0     | 0.69   |
| Maxtor    | 6L020J1            | 20 GB  | 2       | 463   | 3     | 0.69   |
| Maxtor    | STM380815AS        | 80 GB  | 20      | 668   | 665   | 0.69   |
| WDC       | WD800BEVS-22RST0   | 80 GB  | 22      | 419   | 69    | 0.68   |
| WDC       | WD3200AAJS-60M0A0  | 320 GB | 1       | 749   | 2     | 0.68   |
| WDC       | WD60EFRX-68L0BN1   | 6 TB   | 8       | 380   | 5     | 0.68   |
| WDC       | WD5000AAKX-08U6AA0 | 500 GB | 35      | 300   | 6     | 0.68   |
| WDC       | WD2500AAKS-00UU3A0 | 250 GB | 1       | 247   | 0     | 0.68   |
| WDC       | WD30EFRX-68N32N0   | 3 TB   | 1       | 247   | 0     | 0.68   |
| Toshiba   | MK3263GSX          | 320 GB | 5       | 618   | 20    | 0.68   |
| WDC       | WD7501AALS-00E3A0  | 752 GB | 7       | 664   | 52    | 0.68   |
| WDC       | WD2500BEVT-60ZCT1  | 250 GB | 6       | 393   | 10    | 0.68   |
| WDC       | WD2000JS-00MHB1    | 200 GB | 1       | 246   | 0     | 0.68   |
| Hitachi   | HCT721016SLA380    | 160 GB | 3       | 246   | 0     | 0.67   |
| Fujitsu   | MJA2500BH FFS G1   | 500 GB | 1       | 246   | 0     | 0.67   |
| Samsung   | HM320HJ            | 320 GB | 3       | 419   | 422   | 0.67   |
| Seagate   | ST980813AS         | 80 GB  | 1       | 246   | 0     | 0.67   |
| Hitachi   | HDT722516DLA380    | 164 GB | 8       | 845   | 72    | 0.67   |
| Fujitsu   | MHZ2250BH G2       | 250 GB | 11      | 612   | 566   | 0.67   |
| WDC       | WD7500BPVT-22A1YT0 | 752 GB | 1       | 733   | 2     | 0.67   |
| WDC       | WD2502ABYS-18B7A0  | 250 GB | 2       | 244   | 0     | 0.67   |
| WDC       | WD1600BB-00RDA0    | 160 GB | 2       | 691   | 39    | 0.67   |
| WDC       | WD5000BEVT-11A0RT0 | 500 GB | 1       | 243   | 0     | 0.67   |
| Samsung   | SP0411N            | 40 GB  | 1       | 4382  | 17    | 0.67   |
| WDC       | WD10JPVX-60JC3T0   | 1 TB   | 10      | 271   | 81    | 0.67   |
| WDC       | WD5000AAKS-00E4A0  | 500 GB | 7       | 682   | 29    | 0.67   |
| Samsung   | HM320II            | 320 GB | 15      | 403   | 272   | 0.66   |
| Toshiba   | MQ01UBB200         | 2 TB   | 1       | 242   | 0     | 0.66   |
| WDC       | WD5000LPVT-00G33T0 | 500 GB | 5       | 581   | 3     | 0.66   |
| WDC       | WD1600BEVT-75ZCT2  | 160 GB | 12      | 399   | 172   | 0.66   |
| WDC       | WD10EAVS-22D7B0    | 1 TB   | 1       | 2174  | 8     | 0.66   |
| Fujitsu   | MHW2080AT          | 80 GB  | 1       | 241   | 0     | 0.66   |
| Samsung   | MP0402H            | 40 GB  | 3       | 284   | 2     | 0.66   |
| Samsung   | HD322GJ            | 320 GB | 18      | 423   | 68    | 0.66   |
| ExcelStor | J8160S             | 160 GB | 5       | 371   | 3     | 0.66   |
| HGST      | HTS721075A9E630    | 752 GB | 6       | 240   | 0     | 0.66   |
| Seagate   | ST4000VM000-2AF166 | 4 TB   | 1       | 240   | 0     | 0.66   |
| WDC       | WD5000AARS-003BB1  | 500 GB | 4       | 626   | 5     | 0.66   |
| WDC       | WD3200BPVT-24ZEST0 | 320 GB | 20      | 315   | 39    | 0.66   |
| Seagate   | ST380819AS         | 80 GB  | 2       | 799   | 1023  | 0.66   |
| WDC       | WD10EADS-22M2B0    | 1 TB   | 5       | 823   | 8     | 0.66   |
| Toshiba   | MK6034GAX          | 64 GB  | 2       | 879   | 5     | 0.65   |
| Seagate   | ST3120813AS        | 120 GB | 16      | 857   | 717   | 0.65   |
| WDC       | WD800AAJS-00B4A0   | 80 GB  | 3       | 370   | 4     | 0.65   |
| Hitachi   | HTS547550A9E384    | 500 GB | 111     | 381   | 280   | 0.65   |
| WDC       | WD10JPVX-16JC3T3   | 1 TB   | 3       | 237   | 0     | 0.65   |
| Hitachi   | HTS541010G9AT00    | 100 GB | 1       | 474   | 1     | 0.65   |
| Seagate   | ST320410A          | 20 GB  | 3       | 1020  | 17    | 0.65   |
| Hitachi   | HTS725050A7E630    | 500 GB | 8       | 375   | 670   | 0.65   |
| Fujitsu   | MHV2060BH          | 64 GB  | 5       | 469   | 12    | 0.65   |
| Seagate   | ST250LT003-9YG14C  | 250 GB | 3       | 235   | 0     | 0.65   |
| Hitachi   | HTS547564A9E384    | 640 GB | 28      | 518   | 493   | 0.65   |
| Seagate   | ST500LM011 HM501II | 500 GB | 2       | 277   | 1     | 0.64   |
| WDC       | WD3200BEVS-26VAT0  | 320 GB | 1       | 235   | 0     | 0.64   |
| WDC       | WD3200BPVT-16JJ5T0 | 320 GB | 3       | 307   | 1     | 0.64   |
| WDC       | WD5000LPVX-80V0TT0 | 500 GB | 30      | 242   | 1     | 0.64   |
| Samsung   | HM250JI            | 250 GB | 5       | 537   | 9     | 0.64   |
| Toshiba   | MK2035GSS          | 200 GB | 10      | 478   | 27    | 0.64   |
| WDC       | WD3200BEKT-75KA9T0 | 320 GB | 1       | 234   | 0     | 0.64   |
| WDC       | WD5003ABYX-23 0... | 500 GB | 1       | 234   | 0     | 0.64   |
| WDC       | WD5000AADS-67S9B0  | 500 GB | 1       | 2104  | 8     | 0.64   |
| WDC       | WD5000AAKX-75U6AA0 | 500 GB | 5       | 244   | 2     | 0.64   |
| WDC       | WD3200BEVT-00A0RT0 | 320 GB | 15      | 292   | 15    | 0.64   |
| WDC       | WD6400BPVT-26HXZT1 | 640 GB | 1       | 232   | 0     | 0.64   |
| WDC       | WD5000LPVT-24G33T1 | 500 GB | 16      | 316   | 38    | 0.63   |
| WDC       | WD10SPZX-75Z10T1   | 1 TB   | 1       | 231   | 0     | 0.63   |
| WDC       | WD1600BEVT-60ZCT1  | 160 GB | 4       | 354   | 253   | 0.63   |
| Hitachi   | HTS725016A9A364    | 160 GB | 8       | 301   | 383   | 0.63   |
| WDC       | WD5000BPVT-75HXZT3 | 500 GB | 16      | 447   | 3     | 0.63   |
| Seagate   | ST2000VX000-1CU164 | 2 TB   | 10      | 320   | 405   | 0.63   |
| WDC       | WD5000BPVT-22A1YT0 | 500 GB | 7       | 229   | 0     | 0.63   |
| Toshiba   | Generic L200 Ha... | 2 TB   | 2       | 229   | 0     | 0.63   |
| WDC       | WD15EARS-00Z5B1    | 1.5 TB | 21      | 975   | 618   | 0.63   |
| Seagate   | ST3160212ACE       | 160 GB | 4       | 512   | 27    | 0.63   |
| WDC       | WD800BB-98JHC0     | 80 GB  | 1       | 1829  | 7     | 0.63   |
| WDC       | WD10JPVX-22JC3T0   | 1 TB   | 87      | 241   | 18    | 0.63   |
| WDC       | WD80EFZX-68UW8N0   | 8 TB   | 3       | 228   | 0     | 0.63   |
| Seagate   | ST9160821A         | 160 GB | 3       | 412   | 12    | 0.63   |
| WDC       | WD5000BEKT-60KA9T0 | 500 GB | 3       | 324   | 1     | 0.63   |
| Seagate   | ST9160411AS        | 160 GB | 2       | 474   | 14    | 0.63   |
| Hitachi   | HTS545016B9A300    | 160 GB | 35      | 334   | 65    | 0.62   |
| WDC       | WD5000AAKB-00H8A0  | 500 GB | 13      | 568   | 8     | 0.62   |
| Samsung   | HD120IJ            | 120 GB | 18      | 784   | 272   | 0.62   |
| WDC       | WD5000LPVT-08G33T1 | 500 GB | 10      | 237   | 1     | 0.62   |
| WDC       | WD3200LPVX-22V0TT0 | 320 GB | 12      | 255   | 1     | 0.62   |
| WDC       | WD2500YD-01NVB1    | 256 GB | 1       | 1357  | 5     | 0.62   |
| WDC       | WD7500BPVT-75HXZT3 | 752 GB | 3       | 441   | 1     | 0.62   |
| WDC       | WD5000BEKT-80KA9T1 | 500 GB | 4       | 280   | 1     | 0.62   |
| WDC       | WD1005FBYZ-01YCBB2 | 1 TB   | 2       | 225   | 0     | 0.62   |
| Seagate   | ST9750420AS        | 752 GB | 39      | 404   | 91    | 0.62   |
| Samsung   | SP1624N            | 160 GB | 1       | 225   | 0     | 0.62   |
| Seagate   | ST320LM001 HN-M... | 320 GB | 31      | 247   | 1     | 0.62   |
| WDC       | WD6400BPVT-22HXZT1 | 640 GB | 3       | 338   | 3     | 0.62   |
| WDC       | WD10JPVT-75A1YT0   | 1 TB   | 5       | 458   | 4     | 0.62   |
| Seagate   | ST6000VN0041-2E... | 6 TB   | 1       | 224   | 0     | 0.62   |
| Toshiba   | MK5076GSXN         | 500 GB | 1       | 224   | 0     | 0.62   |
| Toshiba   | MQ01ABD032         | 320 GB | 61      | 286   | 64    | 0.61   |
| WDC       | WD3200BEKT-60V5T1  | 320 GB | 21      | 513   | 395   | 0.61   |
| WDC       | WD1600BEVT-00A23T0 | 160 GB | 3       | 277   | 3     | 0.61   |
| WDC       | WD2500AAJS-65M0A0  | 250 GB | 3       | 641   | 13    | 0.61   |
| WDC       | WD3200BEVT-26A23T0 | 320 GB | 2       | 397   | 109   | 0.61   |
| Seagate   | ST3000VX000-1ES166 | 3 TB   | 1       | 222   | 0     | 0.61   |
| Fujitsu   | MHW2120BJ FFS G2   | 120 GB | 1       | 221   | 0     | 0.61   |
| WDC       | WD2000FYYZ-01UL1B1 | 2 TB   | 5       | 276   | 382   | 0.61   |
| WDC       | WD2500AAKS-60VYA0  | 250 GB | 1       | 221   | 0     | 0.61   |
| WDC       | WD2500BEKT-60A25T1 | 250 GB | 7       | 474   | 146   | 0.60   |
| Seagate   | ST9320423AS        | 320 GB | 30      | 450   | 346   | 0.60   |
| WDC       | WD10JPVT-22A1YT0   | 1 TB   | 6       | 314   | 1     | 0.60   |
| Hitachi   | HTS542516K9SA00    | 160 GB | 37      | 591   | 180   | 0.60   |
| Seagate   | ST3160813AS        | 160 GB | 25      | 822   | 171   | 0.60   |
| Seagate   | ST33000651AS       | 3 TB   | 4       | 219   | 0     | 0.60   |
| WDC       | WD3200AAKX-221CA1  | 320 GB | 1       | 218   | 0     | 0.60   |
| WDC       | WD3000HLFS-75G6U1  | 304 GB | 1       | 218   | 0     | 0.60   |
| Maxtor    | 6G160P0            | 160 GB | 2       | 217   | 0     | 0.60   |
| WDC       | WD5000BEVT-22A0RT0 | 500 GB | 30      | 542   | 85    | 0.60   |
| WDC       | WD2500BEVT-22A23T0 | 250 GB | 41      | 397   | 32    | 0.60   |
| Fujitsu   | MJA2160BH G2       | 160 GB | 4       | 420   | 312   | 0.60   |
| WDC       | WD1600JB-00GVC0    | 160 GB | 2       | 777   | 3     | 0.59   |
| WDC       | WD5002AALX-32Z3A0  | 500 GB | 2       | 647   | 1     | 0.59   |
| HGST      | HDN724030ALE640    | 3 TB   | 2       | 216   | 0     | 0.59   |
| Samsung   | HM250HI            | 250 GB | 59      | 320   | 16    | 0.59   |
| WDC       | WD5000AZRZ-00HTKB0 | 500 GB | 7       | 216   | 0     | 0.59   |
| Maxtor    | STM3250820AS       | 250 GB | 9       | 761   | 214   | 0.59   |
| WDC       | WD20EZRX-22D8PB0   | 2 TB   | 1       | 215   | 0     | 0.59   |
| WDC       | WD5000AZDX-00SC2B0 | 500 GB | 3       | 336   | 15    | 0.59   |
| WDC       | WD3200AZDX-00SC2B0 | 320 GB | 2       | 379   | 440   | 0.59   |
| Seagate   | ST9160823ASG       | 160 GB | 2       | 400   | 506   | 0.59   |
| Hitachi   | HDS721050DLE630    | 500 GB | 32      | 495   | 372   | 0.59   |
| WDC       | WD10EZEX-75ZF5A0   | 1 TB   | 4       | 215   | 0     | 0.59   |
| Hitachi   | HDS721010KLA330    | 1 TB   | 5       | 575   | 10    | 0.59   |
| Toshiba   | MK5055GSXN         | 500 GB | 2       | 392   | 4     | 0.59   |
| WDC       | WD10JPVX-80JC3T0   | 1 TB   | 7       | 214   | 0     | 0.59   |
| WDC       | WD10EZEX-75M2NA0   | 1 TB   | 8       | 213   | 0     | 0.58   |
| WDC       | WD5000BEVT-26A0RT0 | 500 GB | 2       | 483   | 321   | 0.58   |
| Fujitsu   | MPE3084AE          | 8 GB   | 1       | 213   | 0     | 0.58   |
| Seagate   | ST2000NM0011       | 2 TB   | 3       | 1091  | 19    | 0.58   |
| Hitachi   | HDT721025SLA380    | 250 GB | 9       | 770   | 117   | 0.58   |
| WDC       | WD1003FBYX-01Y7B1  | 1 TB   | 18      | 365   | 3     | 0.58   |
| Toshiba   | DT01ACA050         | 500 GB | 234     | 243   | 28    | 0.58   |
| Hitachi   | HTS545032A7E380    | 320 GB | 18      | 288   | 117   | 0.58   |
| WDC       | WD7500BPVT-55HXZT4 | 752 GB | 2       | 210   | 0     | 0.58   |
| Seagate   | ST500LM012 HN-M... | 500 GB | 134     | 295   | 50    | 0.57   |
| WDC       | WD10EALX-229BA0    | 1 TB   | 5       | 793   | 11    | 0.57   |
| WDC       | WD5000BEKT-80KA9T0 | 500 GB | 3       | 317   | 1     | 0.57   |
| WDC       | WD800BEVS-00RST0   | 80 GB  | 3       | 277   | 1     | 0.57   |
| Fujitsu   | MHZ2160BH G1       | 160 GB | 7       | 261   | 1     | 0.57   |
| IBM/Hi... | IC35L040AVVN07-0   | 41 GB  | 2       | 576   | 3     | 0.57   |
| WDC       | WD400BB-00FJA0     | 40 GB  | 2       | 699   | 222   | 0.57   |
| Hitachi   | HTS541080G9SA00    | 80 GB  | 6       | 376   | 4     | 0.57   |
| Samsung   | SP0812C            | 80 GB  | 13      | 513   | 161   | 0.57   |
| Seagate   | ST3750528AS        | 752 GB | 37      | 715   | 358   | 0.57   |
| WDC       | WD1600AAJS-75PSA0  | 160 GB | 5       | 353   | 3     | 0.57   |
| Toshiba   | HDWJ110            | 1 TB   | 3       | 207   | 0     | 0.57   |
| WDC       | WD1600BJKT-75F4T0  | 160 GB | 3       | 243   | 1     | 0.57   |
| Samsung   | HN-M320MBB         | 320 GB | 3       | 401   | 3     | 0.57   |
| Seagate   | ST1000LM024 HN-... | 1 TB   | 357     | 290   | 57    | 0.57   |
| Seagate   | ST9120822AS        | 120 GB | 36      | 444   | 451   | 0.57   |
| WDC       | WD10EZEX-00UD2A0   | 1 TB   | 7       | 335   | 125   | 0.56   |
| HGST      | HTS541075A9E680    | 752 GB | 22      | 278   | 418   | 0.56   |
| WDC       | WD10EURS-630AB1    | 1 TB   | 1       | 1846  | 8     | 0.56   |
| WDC       | WD1200JB-00GVC0    | 120 GB | 3       | 539   | 4     | 0.56   |
| Hitachi   | HTS723232L9SA60    | 320 GB | 2       | 292   | 4     | 0.56   |
| WDC       | WD1600BEVS-26VAT0  | 160 GB | 2       | 203   | 0     | 0.56   |
| WDC       | WD20PURX-64P6ZY0   | 2 TB   | 7       | 253   | 21    | 0.56   |
| Seagate   | ST500NM0011        | 500 GB | 9       | 750   | 68    | 0.56   |
| Seagate   | ST96812AS          | 64 GB  | 4       | 327   | 213   | 0.55   |
| WDC       | WD800JD-00JNC0     | 80 GB  | 4       | 451   | 16    | 0.55   |
| Fujitsu   | MHZ2080BH G1       | 80 GB  | 2       | 201   | 0     | 0.55   |
| Seagate   | ST360014A          | 64 GB  | 2       | 757   | 21    | 0.55   |
| WDC       | WD3200BEKX-00B7WT0 | 320 GB | 6       | 203   | 3     | 0.55   |
| Seagate   | ST4000VN000-2AH166 | 4 TB   | 1       | 200   | 0     | 0.55   |
| Seagate   | ST980813ASG        | 80 GB  | 2       | 436   | 6     | 0.55   |
| Seagate   | ST3500312CS        | 500 GB | 12      | 613   | 366   | 0.55   |
| WDC       | WD3200BEVT-22A23T0 | 320 GB | 29      | 478   | 74    | 0.55   |
| Samsung   | SP0802N            | 80 GB  | 24      | 691   | 52    | 0.55   |
| HGST      | HTS721010A9E630    | 1 TB   | 131     | 242   | 81    | 0.55   |
| WDC       | WD1600BEVT-24A23T0 | 160 GB | 11      | 227   | 2     | 0.54   |
| WDC       | WD6400BPVT-00HXZT1 | 640 GB | 3       | 198   | 0     | 0.54   |
| Seagate   | STM3250318AS       | 250 GB | 19      | 478   | 212   | 0.54   |
| WDC       | WD10EADS-11M2B2    | 1 TB   | 1       | 1778  | 8     | 0.54   |
| WDC       | WD5000LPVX-22V0TT0 | 500 GB | 137     | 244   | 14    | 0.54   |
| WDC       | WD6400BPVT-60HXZT1 | 640 GB | 2       | 408   | 42    | 0.54   |
| WDC       | WD1002F9YZ-09H1JL1 | 1 TB   | 2       | 196   | 0     | 0.54   |
| Maxtor    | 6V250F0            | 250 GB | 2       | 196   | 0     | 0.54   |
| WDC       | WD400BD-75MRA1     | 40 GB  | 1       | 196   | 0     | 0.54   |
| WDC       | WD3200BEKT-08PVMT1 | 320 GB | 3       | 195   | 0     | 0.54   |
| Seagate   | ST2000DL001-9VT156 | 2 TB   | 3       | 647   | 673   | 0.54   |
| Quantum   | FIREBALLlct15 30   | 32 GB  | 1       | 391   | 1     | 0.54   |
| Hitachi   | HDS721612PLAT80    | 128 GB | 1       | 1366  | 6     | 0.53   |
| Seagate   | ST94011A           | 40 GB  | 1       | 194   | 0     | 0.53   |
| Seagate   | ST320414A          | 20 GB  | 1       | 194   | 0     | 0.53   |
| Samsung   | HD161HJ            | 160 GB | 36      | 898   | 546   | 0.53   |
| WDC       | WD5000BEVT-00A0RT0 | 500 GB | 9       | 362   | 59    | 0.53   |
| WDC       | WD400BB-00DKA0     | 40 GB  | 1       | 193   | 0     | 0.53   |
| Hitachi   | HTS543232L9A300    | 320 GB | 15      | 644   | 513   | 0.53   |
| Seagate   | ST1000LM014-1EJ164 | 1 TB   | 36      | 308   | 142   | 0.53   |
| Hitachi   | HTS545050A7E380    | 500 GB | 86      | 332   | 126   | 0.53   |
| Toshiba   | MK5065GSXF         | 500 GB | 7       | 340   | 5     | 0.53   |
| Toshiba   | MK2555GSXF         | 250 GB | 4       | 192   | 0     | 0.53   |
| WDC       | WD10PURX-64D85Y0   | 1 TB   | 4       | 388   | 2     | 0.53   |
| WDC       | WD10JPVX-75JC3T0   | 1 TB   | 27      | 222   | 3     | 0.53   |
| WDC       | WD5000LPVX-08V0TT5 | 500 GB | 9       | 211   | 1     | 0.53   |
| Seagate   | ST9500423AS        | 500 GB | 18      | 242   | 7     | 0.52   |
| WDC       | WD5000BPVT-55HXZT3 | 500 GB | 2       | 190   | 0     | 0.52   |
| WDC       | WD4001FAEX-00MJRA0 | 4 TB   | 1       | 190   | 0     | 0.52   |
| Fujitsu   | MHY2160BH          | 160 GB | 8       | 256   | 243   | 0.52   |
| WDC       | WD5000BPVT-26HXZT3 | 500 GB | 1       | 190   | 0     | 0.52   |
| HGST      | HTS541010A9E680    | 1 TB   | 119     | 293   | 261   | 0.52   |
| Hitachi   | HTS723232A7A364    | 320 GB | 22      | 337   | 466   | 0.52   |
| WDC       | WD5000KMVW-11ZSMS5 | 500 GB | 1       | 189   | 0     | 0.52   |
| WDC       | WD7500BPKX-22HPJT0 | 752 GB | 8       | 214   | 2     | 0.52   |
| WDC       | WD10JMVW-11AJGS4   | 1 TB   | 4       | 188   | 0     | 0.52   |
| Seagate   | ST96812A           | 64 GB  | 3       | 379   | 758   | 0.52   |
| Seagate   | ST9500420AS        | 500 GB | 57      | 547   | 430   | 0.51   |
| WDC       | WD10EZEX-00WN4A0   | 1 TB   | 27      | 187   | 0     | 0.51   |
| Hitachi   | HDS721616PLAT80    | 160 GB | 3       | 1226  | 42    | 0.51   |
| WDC       | WD2500BJKT-00F4T0  | 250 GB | 2       | 187   | 0     | 0.51   |
| WDC       | WD800BEVS-75RST0   | 80 GB  | 3       | 438   | 336   | 0.51   |
| Hitachi   | HTS543225A7A384    | 250 GB | 19      | 388   | 334   | 0.51   |
| Toshiba   | MQ02ABD100H        | 1 TB   | 5       | 185   | 0     | 0.51   |
| Seagate   | ST3160812AS 41N... | 160 GB | 1       | 927   | 4     | 0.51   |
| Seagate   | ST2000NM0055-1V... | 2 TB   | 1       | 184   | 0     | 0.51   |
| WDC       | WD5000BEVT-80A0RT0 | 500 GB | 1       | 1662  | 8     | 0.51   |
| Toshiba   | HDWE140            | 4 TB   | 7       | 184   | 0     | 0.51   |
| Seagate   | ST3000DM008-2DM166 | 3 TB   | 10      | 231   | 69    | 0.50   |
| WDC       | WD7500BPVX-60JC3T0 | 752 GB | 3       | 247   | 2     | 0.50   |
| Quantum   | FIREBALLlct15 15   | 15 GB  | 1       | 183   | 0     | 0.50   |
| Seagate   | ST31000523AS       | 1 TB   | 2       | 2094  | 11    | 0.50   |
| Hitachi   | HDT722525DLAT80    | 250 GB | 2       | 733   | 3     | 0.50   |
| Samsung   | HM321HX            | 320 GB | 2       | 263   | 4     | 0.50   |
| Seagate   | ST2000DX001-1CM164 | 2 TB   | 12      | 287   | 301   | 0.50   |
| Toshiba   | MG03ACA300         | 3 TB   | 2       | 322   | 5     | 0.50   |
| IBM/Hi... | IC25N030ATMR04-0   | 32 GB  | 1       | 544   | 2     | 0.50   |
| Hitachi   | HTS541060G9AT00    | 64 GB  | 5       | 479   | 5     | 0.50   |
| WDC       | WD7500BPKT-60PK4T0 | 752 GB | 2       | 343   | 4     | 0.49   |
| HGST      | HUS724040ALA640    | 4 TB   | 1       | 180   | 0     | 0.49   |
| Seagate   | ST3000VN000-1H4167 | 3 TB   | 1       | 179   | 0     | 0.49   |
| Toshiba   | MK8009GAH          | 80 GB  | 2       | 360   | 43    | 0.49   |
| Samsung   | HE753LJ            | 752 GB | 2       | 374   | 51    | 0.49   |
| WDC       | WD2500JS-63MHB5    | 250 GB | 2       | 793   | 39    | 0.49   |
| WDC       | WD5000AAKX-22ERMA0 | 500 GB | 26      | 303   | 3     | 0.49   |
| WDC       | WD6400AADS-00M2B0  | 640 GB | 9       | 795   | 8     | 0.49   |
| WDC       | WD1600BEVT-22A23T0 | 160 GB | 18      | 258   | 5     | 0.49   |
| WDC       | WD2500AAJS-00L7A0  | 250 GB | 22      | 441   | 15    | 0.49   |
| WDC       | WD5000AAKS-08V0A0  | 500 GB | 6       | 441   | 7     | 0.49   |
| Toshiba   | MQ01ABD100         | 1 TB   | 161     | 219   | 49    | 0.49   |
| WDC       | WD5000LPVX-60V0TT0 | 500 GB | 8       | 262   | 22    | 0.48   |
| Seagate   | ST3300822AS        | 304 GB | 1       | 176   | 0     | 0.48   |
| WDC       | WD3200BEVT-24A23T0 | 320 GB | 10      | 529   | 103   | 0.48   |
| Samsung   | HM080HC            | 72 GB  | 1       | 526   | 2     | 0.48   |
| Seagate   | ST980210AS         | 80 GB  | 1       | 175   | 0     | 0.48   |
| WDC       | WD6400BPVT-80HXZT1 | 640 GB | 6       | 421   | 11    | 0.48   |
| WDC       | WD2005FBYZ-01YCBB2 | 2 TB   | 2       | 175   | 0     | 0.48   |
| WDC       | WD2500BPVT-22ZEST0 | 250 GB | 16      | 222   | 4     | 0.48   |
| Hitachi   | HTS541010A9E680    | 1 TB   | 8       | 411   | 902   | 0.48   |
| WDC       | WD2500JD-40HBC0    | 250 GB | 1       | 1391  | 7     | 0.48   |
| Seagate   | ST4000DM005-2DP166 | 4 TB   | 5       | 173   | 0     | 0.48   |
| WDC       | WD1600BEVT-35ZCT0  | 160 GB | 2       | 173   | 0     | 0.48   |
| WDC       | WD2500BEVT-80A23T0 | 250 GB | 17      | 325   | 46    | 0.47   |
| WDC       | WD7500BPVT-08HXZT3 | 752 GB | 3       | 172   | 0     | 0.47   |
| WDC       | WD3200AAKS-22L6A0  | 320 GB | 3       | 378   | 5     | 0.47   |
| Samsung   | HM501II            | 500 GB | 3       | 596   | 5     | 0.47   |
| WDC       | WD5000BPKX-22HPJT0 | 500 GB | 10      | 232   | 1     | 0.47   |
| Seagate   | ST9160827AS        | 160 GB | 29      | 476   | 326   | 0.47   |
| WDC       | WD6400BEVT-22A0RT0 | 640 GB | 7       | 434   | 5     | 0.47   |
| WDC       | WD10EARX-00PASB0   | 1 TB   | 3       | 838   | 26    | 0.47   |
| Seagate   | ST500LM000-1EJ1... | 500 GB | 4       | 170   | 0     | 0.47   |
| Hitachi   | HCS5C1010DLE630    | 1 TB   | 1       | 169   | 0     | 0.47   |
| Toshiba   | MK8046GSX          | 80 GB  | 2       | 299   | 2     | 0.47   |
| WDC       | WD3200BPVT-80ZEST0 | 320 GB | 26      | 355   | 48    | 0.46   |
| WDC       | WD3200BJKT-00F4T0  | 320 GB | 1       | 169   | 0     | 0.46   |
| HP        | VB0250EAVER        | 250 GB | 4       | 949   | 10    | 0.46   |
| Hitachi   | HDS725050KLA360    | 500 GB | 2       | 1300  | 24    | 0.46   |
| Samsung   | HM250HJ            | 250 GB | 2       | 337   | 17    | 0.46   |
| WDC       | WD30EZRZ-00Z5HB0   | 3 TB   | 9       | 168   | 0     | 0.46   |
| Samsung   | HD080HJ-P          | 80 GB  | 8       | 572   | 266   | 0.46   |
| Seagate   | ST1000DM000-9TS15E | 1 TB   | 1       | 168   | 0     | 0.46   |
| WDC       | WD10S21X-24R1BT... | 1 TB   | 5       | 168   | 0     | 0.46   |
| Seagate   | ST9500325ASG       | 500 GB | 2       | 432   | 58    | 0.46   |
| WDC       | WD5000LPCX-24C6HT0 | 500 GB | 35      | 192   | 1     | 0.46   |
| Hitachi   | HDE721010SLA330    | 1 TB   | 2       | 988   | 80    | 0.46   |
| WDC       | WD5000MPCK-60AWHT0 | 500 GB | 1       | 166   | 0     | 0.46   |
| Seagate   | ST3250820NS        | 250 GB | 2       | 695   | 1050  | 0.46   |
| Toshiba   | MK8032GAX          | 80 GB  | 1       | 166   | 0     | 0.46   |
| HGST      | HTS725032A7E630    | 320 GB | 7       | 211   | 439   | 0.45   |
| Seagate   | ST9100824A         | 100 GB | 1       | 165   | 0     | 0.45   |
| WDC       | WD10PURX-64E5EY0   | 1 TB   | 4       | 194   | 1     | 0.45   |
| WDC       | WD800BEVE-00A0HT0  | 80 GB  | 1       | 165   | 0     | 0.45   |
| Seagate   | ST2000LM015-2E8174 | 2 TB   | 7       | 165   | 0     | 0.45   |
| WDC       | WD10SPCX-22HWST0   | 1 TB   | 1       | 165   | 0     | 0.45   |
| WDC       | WD5000LPCX-22VHAT0 | 500 GB | 16      | 164   | 0     | 0.45   |
| Maxtor    | 6G160E0            | 160 GB | 7       | 342   | 129   | 0.45   |
| Hitachi   | HDS721010DLE630    | 1 TB   | 28      | 635   | 598   | 0.45   |
| WDC       | WD2500BPVT-24JJ5T0 | 250 GB | 2       | 164   | 0     | 0.45   |
| WDC       | WD10JFCX-68N6GN0   | 1 TB   | 1       | 163   | 0     | 0.45   |
| Seagate   | ST2000DX002-2DV164 | 2 TB   | 8       | 162   | 0     | 0.45   |
| WDC       | WD5000AAVS-00G9B0  | 500 GB | 1       | 1464  | 8     | 0.45   |
| WDC       | WD2500BEKT-75A25T0 | 250 GB | 2       | 294   | 4     | 0.45   |
| WDC       | WD1600BEVS-22VAT0  | 160 GB | 1       | 324   | 1     | 0.44   |
| Seagate   | ST920217AS         | 20 GB  | 1       | 162   | 0     | 0.44   |
| Seagate   | ST2000DM006-2DM164 | 2 TB   | 19      | 161   | 0     | 0.44   |
| Hitachi   | HTS541616J9SA00    | 160 GB | 26      | 464   | 82    | 0.44   |
| Seagate   | ST8000DM004-2CX188 | 8 TB   | 2       | 161   | 0     | 0.44   |
| Toshiba   | MK8007GAH          | 80 GB  | 2       | 210   | 7     | 0.44   |
| WDC       | WD3200BEVT-00ZCT0  | 320 GB | 4       | 405   | 4     | 0.44   |
| WDC       | WD10JUCT-63J6SY0   | 1 TB   | 5       | 161   | 0     | 0.44   |
| WDC       | WD3200LPCX-24C6HT0 | 320 GB | 19      | 160   | 0     | 0.44   |
| Hitachi   | HTS727575A9E364    | 752 GB | 13      | 408   | 102   | 0.44   |
| Seagate   | ST98823AS          | 80 GB  | 8       | 364   | 520   | 0.44   |
| Toshiba   | MK3265GSXN         | 320 GB | 12      | 428   | 298   | 0.44   |
| WDC       | WD5000BPVT-80HXZT1 | 500 GB | 6       | 569   | 56    | 0.44   |
| WDC       | WD10SPCX-80HWST0   | 1 TB   | 1       | 160   | 0     | 0.44   |
| Hitachi   | HDS722512VLAT20    | 128 GB | 1       | 802   | 4     | 0.44   |
| Seagate   | ST380211AS         | 80 GB  | 7       | 618   | 634   | 0.44   |
| HGST      | HTS725050A7E630    | 500 GB | 98      | 222   | 120   | 0.44   |
| WDC       | WD1600AAJB-22WRA0  | 160 GB | 1       | 1119  | 6     | 0.44   |
| WDC       | WD5000LPVX-28V0TT0 | 500 GB | 1       | 159   | 0     | 0.44   |
| Samsung   | HD082GJ            | 80 GB  | 11      | 499   | 402   | 0.44   |
| WDC       | WD400BB-23FJA0     | 40 GB  | 1       | 796   | 4     | 0.44   |
| WDC       | WD3200BPVT-60JJ5T0 | 320 GB | 9       | 393   | 132   | 0.43   |
| WDC       | WD1600JD-00HBB0    | 160 GB | 4       | 619   | 23    | 0.43   |
| Hitachi   | HTS541075A9E680    | 752 GB | 4       | 325   | 764   | 0.43   |
| WDC       | WD5000BPVT-60HXZT3 | 500 GB | 8       | 543   | 41    | 0.43   |
| Toshiba   | MQ01ABD050V        | 500 GB | 1       | 157   | 0     | 0.43   |
| WDC       | WD7500BPVX-00JC3T0 | 752 GB | 1       | 157   | 0     | 0.43   |
| WDC       | WD1200BEVS-60UST0  | 120 GB | 6       | 475   | 423   | 0.43   |
| Toshiba   | MK3276GSXN         | 320 GB | 1       | 156   | 0     | 0.43   |
| WDC       | WD3200AAJB-00J3A0  | 320 GB | 18      | 340   | 25    | 0.43   |
| WDC       | WD5000LPVX-08V0TT2 | 500 GB | 2       | 276   | 4     | 0.43   |
| WDC       | WD5000BPKT-75PK4T0 | 500 GB | 6       | 306   | 4     | 0.43   |
| WDC       | WD3200BPVT-75ZEST0 | 320 GB | 4       | 675   | 7     | 0.43   |
| Fujitsu   | MHZ2500BT G1       | 500 GB | 1       | 155   | 0     | 0.43   |
| Seagate   | STM9120817AS       | 120 GB | 1       | 155   | 0     | 0.43   |
| Hitachi   | HDP725032GLA380    | 320 GB | 5       | 880   | 41    | 0.43   |
| Hitachi   | HTS543232A7A384    | 320 GB | 139     | 287   | 297   | 0.42   |
| Seagate   | ST1000DM003-1SB102 | 1 TB   | 23      | 155   | 0     | 0.42   |
| WDC       | WD2500BEVT-08A23T1 | 250 GB | 13      | 270   | 133   | 0.42   |
| Seagate   | ST9250827AS        | 250 GB | 22      | 443   | 297   | 0.42   |
| WDC       | WD10JPVX-00JC3T0   | 1 TB   | 28      | 156   | 1     | 0.42   |
| WDC       | WD5000LPVX-55V0TT0 | 500 GB | 11      | 152   | 0     | 0.42   |
| WDC       | WD400JB-00FMA0     | 40 GB  | 1       | 152   | 0     | 0.42   |
| WDC       | WD5000LPCX-00VHAT0 | 500 GB | 19      | 151   | 0     | 0.42   |
| Seagate   | ST9100824AS        | 100 GB | 3       | 195   | 2     | 0.42   |
| Toshiba   | MK1655GSX          | 160 GB | 11      | 331   | 33    | 0.41   |
| Samsung   | HD401LJ            | 400 GB | 3       | 712   | 19    | 0.41   |
| Hitachi   | HTS545050KTA300    | 500 GB | 5       | 469   | 5     | 0.41   |
| Samsung   | SP1634N            | 160 GB | 1       | 298   | 1     | 0.41   |
| Seagate   | ST3160815SV        | 160 GB | 5       | 681   | 1240  | 0.41   |
| Toshiba   | MD03ACA400V        | 4 TB   | 1       | 1037  | 6     | 0.41   |
| Fujitsu   | MHW2020BH          | 20 GB  | 1       | 148   | 0     | 0.41   |
| WDC       | WD1600BEVT-75A23T0 | 160 GB | 3       | 244   | 1     | 0.41   |
| WDC       | WD1200JS-22NCB1    | 120 GB | 1       | 1184  | 7     | 0.41   |
| HGST      | HTS545050A7E380    | 500 GB | 115     | 309   | 242   | 0.40   |
| WDC       | WD5000BEVT-60ZAT1  | 500 GB | 4       | 344   | 15    | 0.40   |
| HGST      | HUS726040ALE614    | 4 TB   | 1       | 147   | 0     | 0.40   |
| Hitachi   | HDS722525VLSA80    | 250 GB | 2       | 370   | 17    | 0.40   |
| Seagate   | ST750LM030-1KKG62  | 752 GB | 2       | 146   | 0     | 0.40   |
| WDC       | WD2500BEVT-00A0RT1 | 245 GB | 1       | 146   | 0     | 0.40   |
| Hitachi   | HDT721064SLA360    | 640 GB | 3       | 1030  | 8     | 0.40   |
| WDC       | WD30PURZ-85GU6Y0   | 3 TB   | 1       | 145   | 0     | 0.40   |
| WDC       | WD3000FYYZ-01UL1B0 | 3 TB   | 1       | 145   | 0     | 0.40   |
| Samsung   | SP0842N            | 80 GB  | 8       | 634   | 591   | 0.40   |
| Toshiba   | MK2555GSX          | 250 GB | 24      | 402   | 91    | 0.40   |
| Fujitsu   | MHV2060BHPL        | 64 GB  | 1       | 144   | 0     | 0.40   |
| WDC       | WD20EZRZ-22Z5HB0   | 2 TB   | 1       | 144   | 0     | 0.40   |
| Seagate   | ST1000VM002-1SD102 | 1 TB   | 1       | 144   | 0     | 0.40   |
| Seagate   | ST1000VX001-1HH162 | 1 TB   | 5       | 144   | 0     | 0.40   |
| Seagate   | ST3750330NS        | 752 GB | 3       | 560   | 337   | 0.39   |
| WDC       | WD3200AAJS-55VWA0  | 320 GB | 1       | 1006  | 6     | 0.39   |
| Toshiba   | HDWN160            | 6 TB   | 1       | 143   | 0     | 0.39   |
| Seagate   | ST3000NM0033-9Z... | 3 TB   | 2       | 577   | 9     | 0.39   |
| WDC       | WD3200AAKX-32ERMA0 | 320 GB | 1       | 142   | 0     | 0.39   |
| Hitachi   | HTS541212H9AT00    | 120 GB | 3       | 438   | 5     | 0.39   |
| Toshiba   | MK5059GSXP         | 500 GB | 24      | 389   | 467   | 0.39   |
| WDC       | WD7500KMVV-11TK7S1 | 752 GB | 1       | 141   | 0     | 0.39   |
| WDC       | WD800BD-22MRA1     | 80 GB  | 2       | 141   | 0     | 0.39   |
| IBM       | DTLA-305020        | 20 GB  | 2       | 1494  | 37    | 0.39   |
| Samsung   | SP2504C            | 250 GB | 30      | 1070  | 826   | 0.39   |
| Toshiba   | MG03ACA100         | 1 TB   | 8       | 165   | 1     | 0.39   |
| Seagate   | ST1500DM003-9YN16G | 1.5 TB | 15      | 468   | 456   | 0.39   |
| WDC       | WD5000AAKX-003CA0  | 500 GB | 13      | 579   | 43    | 0.39   |
| Hitachi   | HTS543216L9A300    | 160 GB | 32      | 545   | 241   | 0.39   |
| WDC       | WD2500AAJB-57WGA0  | 250 GB | 1       | 140   | 0     | 0.38   |
| WDC       | WD800BB-00HEA0     | 80 GB  | 1       | 840   | 5     | 0.38   |
| WDC       | WD2500AAJS-07B4A0  | 250 GB | 2       | 1695  | 198   | 0.38   |
| WDC       | WD400EB-11CPF0     | 40 GB  | 2       | 1019  | 31    | 0.38   |
| WDC       | WD5000BEVT-22ZAT0  | 500 GB | 5       | 425   | 2     | 0.38   |
| WDC       | WD5000AADS-56S9B1  | 500 GB | 4       | 553   | 4     | 0.38   |
| WDC       | WD1600BEVT-80A23T0 | 160 GB | 18      | 194   | 22    | 0.38   |
| Seagate   | ST1000DM003-1SB10C | 1 TB   | 40      | 141   | 1     | 0.38   |
| Hitachi   | HTS542512K9SA00    | 120 GB | 48      | 506   | 113   | 0.38   |
| Seagate   | ST320LT022-1AE142  | 320 GB | 1       | 138   | 0     | 0.38   |
| Toshiba   | HDWA120            | 2 TB   | 3       | 138   | 0     | 0.38   |
| Seagate   | ST9320325AS        | 320 GB | 185     | 431   | 446   | 0.37   |
| Toshiba   | MK8037GSX          | 80 GB  | 15      | 456   | 158   | 0.37   |
| Seagate   | ST320LT007-9ZV142  | 320 GB | 18      | 426   | 810   | 0.37   |
| WDC       | WD2500AAKX-603CA0  | 250 GB | 3       | 138   | 401   | 0.37   |
| Seagate   | ST3120811AS        | 120 GB | 13      | 517   | 396   | 0.37   |
| Hitachi   | HCT721050SLA380    | 500 GB | 1       | 136   | 0     | 0.37   |
| WDC       | WD1600AAJS-60Z0A0  | 160 GB | 3       | 233   | 12    | 0.37   |
| Toshiba   | HDWD110            | 1 TB   | 74      | 140   | 7     | 0.37   |
| HGST      | HTS545032A7E380    | 320 GB | 18      | 234   | 62    | 0.37   |
| Toshiba   | HDWD120            | 2 TB   | 11      | 135   | 0     | 0.37   |
| WDC       | WD10SPCX-24HWST1   | 1 TB   | 6       | 134   | 0     | 0.37   |
| WDC       | WD800JD-00JNA0     | 80 GB  | 2       | 809   | 5     | 0.37   |
| Hitachi   | HTS541680J9SA00    | 80 GB  | 43      | 466   | 36    | 0.37   |
| Toshiba   | MK6475GSX          | 640 GB | 17      | 299   | 395   | 0.37   |
| Toshiba   | MK7575GSX          | 752 GB | 17      | 507   | 585   | 0.37   |
| Hitachi   | HCS5C1032CLA382    | 320 GB | 1       | 673   | 4     | 0.37   |
| WDC       | WD3201ABYS-01B9A0  | 320 GB | 2       | 926   | 278   | 0.37   |
| WDC       | WD3200AAKX-073CA1  | 320 GB | 2       | 342   | 4     | 0.37   |
| WDC       | WD6400BPVT-75HXZT1 | 640 GB | 2       | 385   | 3     | 0.37   |
| Seagate   | ST9750423AS        | 752 GB | 8       | 317   | 253   | 0.37   |
| Toshiba   | MK5076GSX -63      | 500 GB | 2       | 134   | 0     | 0.37   |
| Seagate   | ST3200822A         | 200 GB | 3       | 1664  | 14    | 0.37   |
| Fujitsu   | MJA2320BH G2       | 320 GB | 4       | 669   | 521   | 0.37   |
| WDC       | WD1600AAJS-98PSA0  | 160 GB | 1       | 401   | 2     | 0.37   |
| Toshiba   | MQ01ABF032         | 320 GB | 17      | 180   | 61    | 0.37   |
| WDC       | WD1600AAJB-00J3A0  | 160 GB | 14      | 573   | 153   | 0.36   |
| Toshiba   | MQ01ABD050         | 500 GB | 82      | 302   | 327   | 0.36   |
| WDC       | WD1600AVVS-63L2B0  | 160 GB | 3       | 132   | 0     | 0.36   |
| IBM/Hi... | IC35L040AVER07-0   | 41 GB  | 2       | 1050  | 7     | 0.36   |
| WDC       | WD10EARX-00NYB0    | 1 TB   | 1       | 130   | 0     | 0.36   |
| Toshiba   | MK7559GSXP         | 752 GB | 13      | 428   | 411   | 0.36   |
| Maxtor    | STM3160215A        | 160 GB | 6       | 209   | 512   | 0.36   |
| WDC       | WD5000AAKS-00V6A0  | 500 GB | 3       | 1286  | 15    | 0.36   |
| Seagate   | ST9120822A         | 120 GB | 2       | 273   | 53    | 0.36   |
| WDC       | WD10EZRZ-00HTKB0   | 1 TB   | 25      | 144   | 1     | 0.36   |
| Hitachi   | HTS542525K9SA00    | 250 GB | 29      | 537   | 79    | 0.36   |
| Toshiba   | MQ01ACF050         | 500 GB | 6       | 157   | 173   | 0.36   |
| Samsung   | SP0822N            | 80 GB  | 6       | 130   | 1     | 0.35   |
| WDC       | WD5001AALS-00LWTA0 | 500 GB | 4       | 522   | 62    | 0.35   |
| WDC       | WD10EADS-98M2B0    | 1 TB   | 1       | 899   | 6     | 0.35   |
| WDC       | WD800JD-22LSA1     | 80 GB  | 4       | 485   | 174   | 0.35   |
| WDC       | WD3200AAJS-65M0A0  | 320 GB | 1       | 1152  | 8     | 0.35   |
| WDC       | WD1200JB-00FUA0    | 120 GB | 1       | 128   | 0     | 0.35   |
| Samsung   | HM500JJ            | 500 GB | 2       | 331   | 5     | 0.35   |
| Samsung   | SP2004C            | 200 GB | 26      | 668   | 489   | 0.35   |
| Toshiba   | MK1034GSX          | 100 GB | 4       | 418   | 464   | 0.35   |
| Seagate   | ST500DM002-9YN14C  | 500 GB | 3       | 464   | 339   | 0.35   |
| Seagate   | ST95005620AS       | 500 GB | 7       | 374   | 299   | 0.35   |
| Seagate   | ST3500830SCE       | 500 GB | 1       | 126   | 0     | 0.35   |
| Seagate   | ST9120821AS        | 120 GB | 5       | 274   | 1101  | 0.35   |
| WDC       | WD400BB-60DGA0     | 40 GB  | 1       | 504   | 3     | 0.35   |
| WDC       | WD3200BEVT-26ZCT0  | 320 GB | 4       | 160   | 1     | 0.35   |
| WDC       | WD5000LPVX-75V0TT0 | 500 GB | 19      | 156   | 2     | 0.34   |
| Seagate   | ST3250312CS        | 250 GB | 11      | 317   | 230   | 0.34   |
| Toshiba   | MK1216GSG          | 120 GB | 3       | 272   | 4     | 0.34   |
| Seagate   | ST500LT015-1DJ142  | 500 GB | 1       | 124   | 0     | 0.34   |
| Seagate   | ST1000VX000-1ES162 | 1 TB   | 15      | 124   | 0     | 0.34   |
| WDC       | WD20EARS-00J2GB0   | 2 TB   | 1       | 1120  | 8     | 0.34   |
| WDC       | WD3200AAKS-00C9A0  | 320 GB | 3       | 1080  | 8     | 0.34   |
| Seagate   | ST9250315AS        | 250 GB | 150     | 470   | 439   | 0.34   |
| Hitachi   | HTS725050A9A364    | 500 GB | 14      | 405   | 676   | 0.34   |
| Toshiba   | MK3252GSX          | 320 GB | 16      | 573   | 246   | 0.34   |
| WDC       | WD5000AAKX-60U6AA0 | 500 GB | 25      | 208   | 136   | 0.34   |
| WDC       | WD3200BEVT-08A23T1 | 320 GB | 3       | 203   | 3     | 0.34   |
| Seagate   | ST320DM001 HD322GJ | 320 GB | 4       | 187   | 108   | 0.33   |
| Hitachi   | HTS545025B9SA02    | 250 GB | 5       | 153   | 405   | 0.33   |
| WDC       | WD3200AAJS-56M0A0  | 320 GB | 6       | 357   | 2     | 0.33   |
| Toshiba   | MK3259GSXP         | 320 GB | 42      | 294   | 122   | 0.33   |
| HGST      | HTS541010A7E630    | 1 TB   | 11      | 132   | 1     | 0.33   |
| WDC       | WD2500BEVE-00A0HT0 | 250 GB | 1       | 120   | 0     | 0.33   |
| Hitachi   | HTS541080G9AT00    | 80 GB  | 11      | 495   | 75    | 0.33   |
| WDC       | WD3200AVJS-63B6A0  | 320 GB | 4       | 1168  | 26    | 0.33   |
| Seagate   | ST9100827AS        | 100 GB | 1       | 838   | 6     | 0.33   |
| WDC       | WD5001AALS-00J7B1  | 500 GB | 1       | 1077  | 8     | 0.33   |
| Seagate   | ST910021AS         | 100 GB | 6       | 552   | 547   | 0.33   |
| Seagate   | ST960821A          | 64 GB  | 1       | 358   | 2     | 0.33   |
| Toshiba   | MK6025GAS          | 64 GB  | 2       | 166   | 9     | 0.33   |
| Seagate   | ST9320310AS        | 320 GB | 6       | 465   | 468   | 0.33   |
| Seagate   | ST340810A          | 40 GB  | 8       | 468   | 38    | 0.33   |
| WDC       | WD2500BPVT-75JJ5T0 | 250 GB | 2       | 117   | 0     | 0.32   |
| WDC       | WD5000BPVT-08HXZT1 | 500 GB | 1       | 117   | 0     | 0.32   |
| Toshiba   | MK1633GSG          | 160 GB | 2       | 116   | 0     | 0.32   |
| Hitachi   | HTS727550A9E364    | 500 GB | 7       | 324   | 440   | 0.32   |
| WDC       | 500GB              | 500 GB | 1       | 1047  | 8     | 0.32   |
| Seagate   | ST640LM001 HN-M... | 640 GB | 1       | 116   | 0     | 0.32   |
| Toshiba   | MQ01ABF050         | 500 GB | 210     | 138   | 86    | 0.32   |
| Toshiba   | MK2546GSX          | 250 GB | 12      | 520   | 41    | 0.32   |
| Hitachi   | HTS543216L9SA00    | 160 GB | 9       | 295   | 11    | 0.32   |
| WDC       | WD5003ABYZ-011FA0  | 500 GB | 4       | 197   | 2     | 0.32   |
| Toshiba   | MK1237GSX          | 120 GB | 10      | 353   | 28    | 0.32   |
| Seagate   | ST9250315ASG       | 250 GB | 1       | 115   | 0     | 0.32   |
| WDC       | WD5000AAKS-00M9A0  | 500 GB | 4       | 580   | 569   | 0.31   |
| Toshiba   | MK2565GSX          | 250 GB | 15      | 250   | 223   | 0.31   |
| WDC       | WD3200AVJS-63N9A0  | 320 GB | 1       | 114   | 0     | 0.31   |
| WDC       | WD5000LPLX-00ZNTT0 | 500 GB | 29      | 113   | 0     | 0.31   |
| WDC       | WD10EZEX-08Y20A0   | 1 TB   | 5       | 113   | 0     | 0.31   |
| WDC       | WD10EZEX-07M2NA0   | 1 TB   | 2       | 773   | 9     | 0.31   |
| Seagate   | ST4000DX001-1CE168 | 4 TB   | 5       | 130   | 5     | 0.31   |
| WDC       | WD3200AAKS-00YGA0  | 320 GB | 1       | 562   | 4     | 0.31   |
| WDC       | WD4003FZEX-00Z4SA0 | 4 TB   | 1       | 112   | 0     | 0.31   |
| Seagate   | ST3320311CS        | 320 GB | 4       | 194   | 252   | 0.31   |
| Seagate   | ST9100823A         | 96 GB  | 1       | 1007  | 8     | 0.31   |
| Seagate   | ST500LT012-1DG142  | 500 GB | 290     | 166   | 61    | 0.31   |
| Toshiba   | MK8034GSX          | 80 GB  | 8       | 324   | 38    | 0.30   |
| WDC       | WD40NMZW-11GX6S1   | 4 TB   | 1       | 111   | 0     | 0.30   |
| WDC       | WD400EB-00CPF0     | 40 GB  | 2       | 534   | 11    | 0.30   |
| WDC       | WD10EZEX-21WN4A0   | 1 TB   | 11      | 124   | 1     | 0.30   |
| WDC       | WD2500BEVT-75A23T0 | 250 GB | 5       | 581   | 13    | 0.30   |
| WDC       | WD2500BEVT-00ZCT0  | 250 GB | 6       | 110   | 0     | 0.30   |
| Toshiba   | MK1637GSX          | 160 GB | 26      | 517   | 59    | 0.30   |
| Hitachi   | HTS542580K9SA00    | 80 GB  | 8       | 296   | 5     | 0.30   |
| Seagate   | ST9500325AS        | 500 GB | 280     | 448   | 596   | 0.30   |
| WDC       | WD5000AZLX-00K2TA0 | 500 GB | 7       | 109   | 0     | 0.30   |
| WDC       | WD20EADS-32S2B0    | 2 TB   | 1       | 1198  | 10    | 0.30   |
| WDC       | WD10JPVX-35JC3T0   | 1 TB   | 2       | 108   | 0     | 0.30   |
| WDC       | WD10JMVW-11S5XS0   | 1 TB   | 1       | 108   | 0     | 0.30   |
| WDC       | WD7500BPVT-00HXZT3 | 752 GB | 8       | 457   | 14    | 0.30   |
| WDC       | WD2500LPCX-24C6HT0 | 250 GB | 33      | 133   | 65    | 0.30   |
| Toshiba   | MK3276GSX -63      | 320 GB | 5       | 178   | 1     | 0.29   |
| Seagate   | ST980811AS         | 80 GB  | 15      | 418   | 319   | 0.29   |
| WDC       | WD10TMVW-11ZSMS4   | 1 TB   | 1       | 107   | 0     | 0.29   |
| WDC       | WD3200AAJS-60M0A1  | 320 GB | 3       | 596   | 1255  | 0.29   |
| Fujitsu   | MHW2040BH          | 40 GB  | 1       | 214   | 1     | 0.29   |
| Toshiba   | HDWD130            | 3 TB   | 5       | 106   | 0     | 0.29   |
| Fujitsu   | MHV2100BH PL       | 100 GB | 3       | 291   | 4     | 0.29   |
| Hitachi   | HTS542520K9SA00    | 200 GB | 4       | 658   | 11    | 0.29   |
| China     | TP00250GB          | 250 GB | 1       | 106   | 0     | 0.29   |
| Seagate   | ST9160314AS        | 160 GB | 25      | 292   | 190   | 0.29   |
| Toshiba   | MD04ACA500         | 5 TB   | 2       | 105   | 0     | 0.29   |
| Seagate   | ST320LT020-9YG142  | 320 GB | 107     | 333   | 569   | 0.29   |
| Hitachi   | HDS721616PLA320    | 160 GB | 1       | 1586  | 14    | 0.29   |
| Toshiba   | MK1059GSMP         | 1 TB   | 12      | 472   | 308   | 0.29   |
| Seagate   | ST3500410AS        | 500 GB | 23      | 1001  | 367   | 0.29   |
| Seagate   | ST3500412AS        | 500 GB | 17      | 858   | 589   | 0.29   |
| WDC       | WD5000LPVX-00V0TT0 | 500 GB | 14      | 156   | 54    | 0.29   |
| WDC       | WD5000AAKS-55V0A0  | 500 GB | 6       | 391   | 7     | 0.29   |
| WDC       | WD10TMVW-11ZSMS5   | 1 TB   | 2       | 130   | 5     | 0.29   |
| Hitachi   | HTS725032A9A364    | 320 GB | 13      | 448   | 888   | 0.29   |
| Toshiba   | MK6006GAH          | 64 GB  | 1       | 103   | 0     | 0.28   |
| WDC       | WD5000AAKX-19U6AA0 | 500 GB | 1       | 103   | 0     | 0.28   |
| WDC       | WD1600BEVT-60ZCT0  | 160 GB | 5       | 203   | 403   | 0.28   |
| Samsung   | HN-M101MBB         | 1 TB   | 9       | 450   | 371   | 0.28   |
| WDC       | WD5000LPCX-60VHAT0 | 500 GB | 17      | 122   | 1     | 0.28   |
| Fujitsu   | MHV2080BH PL       | 80 GB  | 9       | 214   | 5     | 0.28   |
| Fujitsu   | MHT2040AH PL       | 40 GB  | 1       | 306   | 2     | 0.28   |
| WDC       | WD10EZRX-22A3KB0   | 1 TB   | 1       | 101   | 0     | 0.28   |
| Samsung   | SP1604N            | 160 GB | 3       | 394   | 62    | 0.28   |
| WDC       | WD5000AACS-00G8B0  | 500 GB | 4       | 911   | 8     | 0.28   |
| WDC       | WD3202ABYS-01B7A0  | 320 GB | 3       | 581   | 5     | 0.28   |
| WDC       | WD5000AVCS-632DY1  | 500 GB | 3       | 167   | 1     | 0.28   |
| WDC       | WD10EADS-65P6B0    | 1 TB   | 1       | 907   | 8     | 0.28   |
| WDC       | WD5000HHTZ-04N21V1 | 500 GB | 1       | 100   | 0     | 0.27   |
| WDC       | WD10SPCX-75HWST0   | 1 TB   | 1       | 100   | 0     | 0.27   |
| Seagate   | ST3400620NS        | 400 GB | 1       | 2185  | 21    | 0.27   |
| Samsung   | HD252KJ            | 250 GB | 7       | 730   | 436   | 0.27   |
| Toshiba   | HDWN180            | 8 TB   | 2       | 99    | 0     | 0.27   |
| Seagate   | ST320LT012-1DG14C  | 320 GB | 18      | 196   | 64    | 0.27   |
| Seagate   | ST500LM000-SSHD... | 500 GB | 16      | 179   | 142   | 0.27   |
| Hitachi   | HDP725016GLA380    | 160 GB | 6       | 671   | 260   | 0.27   |
| Hitachi   | HTS541612J9SA00    | 120 GB | 49      | 537   | 59    | 0.27   |
| HGST      | HTS545050A7E660    | 500 GB | 10      | 181   | 4     | 0.27   |
| Toshiba   | MG04ACA200E        | 2 TB   | 3       | 105   | 3     | 0.27   |
| Toshiba   | MK3265GSX          | 320 GB | 48      | 595   | 248   | 0.26   |
| WDC       | WD1200BEVS-60RST0  | 120 GB | 1       | 766   | 7     | 0.26   |
| Seagate   | ST320LM010-1KJ15C  | 320 GB | 3       | 496   | 6     | 0.26   |
| Samsung   | SP0401N            | 40 GB  | 1       | 95    | 0     | 0.26   |
| Seagate   | ST380023A          | 80 GB  | 1       | 2869  | 29    | 0.26   |
| Samsung   | HD200HJ            | 200 GB | 14      | 867   | 739   | 0.26   |
| WDC       | WD40EFRX-68N32N0   | 4 TB   | 12      | 101   | 1     | 0.26   |
| Seagate   | ST9160821AS        | 160 GB | 42      | 453   | 675   | 0.26   |
| Seagate   | ST1000DM010-2DM162 | 1 TB   | 1       | 95    | 0     | 0.26   |
| Fujitsu   | MHV2060AT          | 64 GB  | 1       | 854   | 8     | 0.26   |
| Seagate   | ST3000DM001-9YN166 | 3 TB   | 13      | 474   | 1318  | 0.26   |
| Toshiba   | MK5065GSX          | 500 GB | 14      | 312   | 217   | 0.26   |
| MediaMax  | WL320GLSA854G      | 320 GB | 1       | 94    | 0     | 0.26   |
| WDC       | WD1003FZEX-00K3CA0 | 1 TB   | 9       | 94    | 0     | 0.26   |
| Seagate   | ST1000UM000-1EK164 | 1 TB   | 1       | 94    | 0     | 0.26   |
| Toshiba   | MK1665GSX H        | 160 GB | 1       | 93    | 0     | 0.26   |
| WDC       | WD10EZRZ-00Z5HB0   | 1 TB   | 4       | 93    | 0     | 0.26   |
| WDC       | WD3200BEVT-00A23T0 | 320 GB | 3       | 146   | 9     | 0.26   |
| WDC       | WD7500BPVT-22HXZT1 | 752 GB | 4       | 831   | 260   | 0.25   |
| WDC       | WD40PURX-64NZ6Y0   | 4 TB   | 1       | 92    | 0     | 0.25   |
| Seagate   | ST9160823AS        | 160 GB | 5       | 1026  | 670   | 0.25   |
| WDC       | WD2500JS-19NCB1    | 250 GB | 1       | 92    | 0     | 0.25   |
| WDC       | WD20EZRZ-00Z5HB0   | 2 TB   | 13      | 92    | 0     | 0.25   |
| WDC       | WD5000AZLX-21K2TA0 | 500 GB | 3       | 91    | 0     | 0.25   |
| Seagate   | ST3320613AS        | 320 GB | 81      | 791   | 245   | 0.25   |
| Toshiba   | MK1246GSX          | 120 GB | 13      | 396   | 53    | 0.25   |
| WDC       | WD1600BPVT-22JJ5T0 | 160 GB | 1       | 91    | 0     | 0.25   |
| HP        | GB0250EAFJF        | 250 GB | 1       | 634   | 6     | 0.25   |
| WDC       | WD8000AARS-00Y5B1  | 800 GB | 1       | 811   | 8     | 0.25   |
| WDC       | WD10JPVX-60JC3T1   | 1 TB   | 10      | 97    | 8     | 0.25   |
| Seagate   | ST31000340SV       | 1 TB   | 1       | 1616  | 17    | 0.25   |
| Hitachi   | HTS541616J9AT00    | 160 GB | 2       | 356   | 7     | 0.25   |
| Samsung   | HS082HB            | 80 GB  | 1       | 89    | 0     | 0.25   |
| WDC       | WD10EZEX-35WN4A0   | 1 TB   | 3       | 88    | 0     | 0.24   |
| WDC       | WD3200AAKX-753CA1  | 320 GB | 2       | 221   | 4     | 0.24   |
| WDC       | WD5000LPCX-21VHAT0 | 500 GB | 37      | 88    | 0     | 0.24   |
| WDC       | WD5000AZLX-00CL5A0 | 500 GB | 3       | 88    | 0     | 0.24   |
| Toshiba   | MK6465GSX          | 640 GB | 19      | 624   | 706   | 0.24   |
| Samsung   | HN-M750MBB         | 752 GB | 4       | 229   | 7     | 0.24   |
| WDC       | WD10EADS-65M2B0    | 1 TB   | 1       | 1319  | 14    | 0.24   |
| WDC       | WD5000AAKS-65V0A0  | 500 GB | 2       | 786   | 8     | 0.24   |
| Seagate   | ST340014AS         | 40 GB  | 3       | 848   | 678   | 0.24   |
| WDC       | WD1600JS-61MHB1    | 160 GB | 1       | 959   | 10    | 0.24   |
| WDC       | WD2000JB-22GVA0    | 200 GB | 1       | 694   | 7     | 0.24   |
| WDC       | WD1600BEVT-00A1TT0 | 160 GB | 2       | 273   | 3     | 0.24   |
| Hitachi   | HTS541010G9SA00    | 100 GB | 10      | 359   | 13    | 0.24   |
| WDC       | WD1600AAJS-56M0A0  | 160 GB | 1       | 770   | 8     | 0.23   |
| WDC       | WD800BB-55JKC0     | 80 GB  | 6       | 677   | 26    | 0.23   |
| Seagate   | ST8000VN0022-2E... | 8 TB   | 1       | 85    | 0     | 0.23   |
| Samsung   | HD300LD            | 304 GB | 4       | 554   | 15    | 0.23   |
| HGST      | HTS545050A7E680    | 500 GB | 172     | 168   | 342   | 0.23   |
| Seagate   | ST1000LM014-SSH... | 1 TB   | 9       | 266   | 179   | 0.23   |
| WDC       | WD5000AAKS-60WWPA0 | 500 GB | 5       | 519   | 669   | 0.23   |
| Toshiba   | MQ04UBF100         | 1 TB   | 2       | 83    | 0     | 0.23   |
| WDC       | WD10EZEX-60WN4A0   | 1 TB   | 21      | 111   | 49    | 0.23   |
| HGST      | HUS726T4TALN6L4    | 4 TB   | 1       | 83    | 0     | 0.23   |
| Toshiba   | MK3021GAS          | 32 GB  | 1       | 495   | 5     | 0.23   |
| WDC       | WD5000LPLX-75ZNTT0 | 500 GB | 3       | 82    | 0     | 0.23   |
| WDC       | WD2500AAKX-193CA0  | 250 GB | 1       | 82    | 0     | 0.23   |
| WDC       | WD20EARS-22MVWB0   | 2 TB   | 1       | 739   | 8     | 0.23   |
| Seagate   | ST9250410ASG       | 250 GB | 1       | 409   | 4     | 0.22   |
| WDC       | WD1600JD-41HBC0    | 160 GB | 1       | 1884  | 22    | 0.22   |
| WDC       | WD50EFRX-68MYMN1   | 5 TB   | 2       | 81    | 0     | 0.22   |
| Hitachi   | HTS541060G9SA00    | 64 GB  | 2       | 420   | 5     | 0.22   |
| WDC       | WD5000AAKS-00H2B0  | 499 GB | 1       | 731   | 8     | 0.22   |
| WDC       | WD10EURX-73C57Y0   | 1 TB   | 1       | 81    | 0     | 0.22   |
| Seagate   | ST500DM002-1SB10A  | 500 GB | 17      | 84    | 1     | 0.22   |
| WDC       | WD10EZEX-08WN4A0   | 1 TB   | 77      | 82    | 1     | 0.22   |
| WDC       | WD1600JS-22NCB1    | 160 GB | 3       | 535   | 7     | 0.22   |
| WDC       | WD10J31X-00U3VT0   | 1 TB   | 1       | 80    | 0     | 0.22   |
| Seagate   | ST9160310AS        | 160 GB | 27      | 276   | 202   | 0.22   |
| Magnet... | MD03200-AJDW-RO    | 320 GB | 1       | 79    | 0     | 0.22   |
| Hitachi   | HTS541040G9AT00    | 40 GB  | 3       | 249   | 5     | 0.22   |
| Seagate   | ST250LM004 HN-M... | 250 GB | 4       | 245   | 9     | 0.22   |
| Fujitsu   | MJA2500BH G2       | 500 GB | 9       | 290   | 130   | 0.22   |
| Seagate   | ST1000DM010-2EP102 | 1 TB   | 73      | 84    | 3     | 0.22   |
| WDC       | WD600BEVS-07LAT0   | 64 GB  | 1       | 635   | 7     | 0.22   |
| WDC       | WD400BB-75JHC0     | 40 GB  | 1       | 476   | 5     | 0.22   |
| WDC       | WD3200BUCT-63TWBY0 | 320 GB | 2       | 79    | 0     | 0.22   |
| WDC       | WD7500BPKX-00HPJT0 | 752 GB | 4       | 78    | 0     | 0.22   |
| Maxtor    | STM380211AS        | 80 GB  | 4       | 271   | 874   | 0.21   |
| Toshiba   | HDWD105            | 500 GB | 43      | 84    | 46    | 0.21   |
| WDC       | WD1600BEVT-26ZCT0  | 160 GB | 1       | 78    | 0     | 0.21   |
| WDC       | WD5000AZRX-00A3KB0 | 500 GB | 3       | 114   | 3     | 0.21   |
| Hitachi   | HTS543232L9SA00    | 320 GB | 7       | 468   | 132   | 0.21   |
| Seagate   | ST500LM000-1EJ162  | 500 GB | 36      | 164   | 52    | 0.21   |
| WDC       | WD7500LPCX-60KHST0 | 752 GB | 3       | 77    | 0     | 0.21   |
| WDC       | WD10EFRX-68FYTN0   | 1 TB   | 11      | 96    | 1     | 0.21   |
| Fujitsu   | MHV2060BH PL       | 64 GB  | 3       | 76    | 3     | 0.21   |
| Toshiba   | MG04ACA400E        | 4 TB   | 2       | 76    | 0     | 0.21   |
| Fujitsu   | MHV2060AT PL       | 64 GB  | 3       | 851   | 16    | 0.21   |
| WDC       | WD2502ABYS-50B7A1  | 250 GB | 1       | 1290  | 16    | 0.21   |
| Hitachi   | HTS543280L9A300    | 80 GB  | 2       | 99    | 1     | 0.21   |
| WDC       | WD1004FBYZ-01YCBB1 | 1 TB   | 1       | 75    | 0     | 0.21   |
| Toshiba   | MK6476GSXN         | 640 GB | 3       | 122   | 601   | 0.21   |
| WDC       | WD3200BPVT-00ZEST0 | 320 GB | 2       | 74    | 0     | 0.21   |
| WDC       | WD5000LPCX-24VHAT0 | 500 GB | 37      | 75    | 30    | 0.20   |
| WDC       | WD2500BPVT-22JJ5T0 | 250 GB | 5       | 327   | 189   | 0.20   |
| WDC       | WD400VE-07HDT0     | 40 GB  | 1       | 74    | 0     | 0.20   |
| Seagate   | ST9320320AS        | 320 GB | 18      | 746   | 140   | 0.20   |
| WDC       | WD800VE-75HDT1     | 80 GB  | 1       | 369   | 4     | 0.20   |
| Hitachi   | HDE721050SLA330    | 500 GB | 1       | 2416  | 32    | 0.20   |
| WDC       | WD1500BLHX-01V7BV0 | 150 GB | 1       | 72    | 0     | 0.20   |
| WDC       | WD1600SD-01KCC0    | 160 GB | 1       | 2914  | 39    | 0.20   |
| WDC       | WD10JMVW-11S5XS1   | 1 TB   | 1       | 72    | 0     | 0.20   |
| Samsung   | SP2514N            | 250 GB | 6       | 419   | 509   | 0.20   |
| Seagate   | ST9120411ASG       | 120 GB | 1       | 361   | 4     | 0.20   |
| WDC       | WD20NMVW-11AV3S4   | 2 TB   | 2       | 751   | 512   | 0.20   |
| WDC       | WD10JPCX-24UE4T0   | 1 TB   | 19      | 99    | 2     | 0.20   |
| Seagate   | ST9120817AS        | 120 GB | 4       | 433   | 595   | 0.20   |
| HP        | MB1000EAMZE        | 1 TB   | 1       | 1919  | 26    | 0.19   |
| Fujitsu   | MHW2160BH          | 160 GB | 2       | 411   | 45    | 0.19   |
| IBM       | DTLA-307015        | 15 GB  | 1       | 423   | 5     | 0.19   |
| WDC       | WD7500BPVX-75JC3T0 | 752 GB | 1       | 349   | 4     | 0.19   |
| WDC       | WD5000LPLX-08ZNTT0 | 500 GB | 3       | 69    | 0     | 0.19   |
| Seagate   | ST9160301AS        | 160 GB | 5       | 153   | 403   | 0.19   |
| Seagate   | ST1000LM025 HN-... | 1 TB   | 6       | 69    | 0     | 0.19   |
| WDC       | WD10EZEX-22MFCA0   | 1 TB   | 19      | 72    | 1     | 0.19   |
| WDC       | WD5000LPLX-22ZNTT0 | 500 GB | 4       | 69    | 0     | 0.19   |
| WDC       | WD3200BPVT-00HXZT1 | 320 GB | 5       | 377   | 208   | 0.19   |
| Seagate   | ST380021A          | 80 GB  | 8       | 725   | 38    | 0.19   |
| Hitachi   | HTS722020K9SA00    | 200 GB | 3       | 636   | 9     | 0.19   |
| Toshiba   | MK3263GSXN         | 320 GB | 7       | 558   | 26    | 0.19   |
| HGST      | HTE725050A7E630    | 500 GB | 2       | 68    | 0     | 0.19   |
| Hitachi   | HTS542525K9A300    | 250 GB | 2       | 372   | 511   | 0.19   |
| WDC       | WD5000BMVW-11AJGS4 | 500 GB | 2       | 76    | 281   | 0.19   |
| WDC       | WD3200BEVT-60A23T0 | 320 GB | 16      | 265   | 344   | 0.19   |
| WDC       | WD2500AAJS-22L7A0  | 250 GB | 3       | 625   | 9     | 0.19   |
| Seagate   | ST2000LM005 HN-... | 2 TB   | 1       | 67    | 0     | 0.19   |
| Seagate   | ST91608220AS       | 160 GB | 1       | 135   | 1     | 0.19   |
| WDC       | WD200BB-60CJA0     | 20 GB  | 1       | 1417  | 20    | 0.18   |
| WDC       | WD3200JS-22PDB0    | 320 GB | 1       | 1538  | 22    | 0.18   |
| WDC       | WD10EZEX-75WN4A0   | 1 TB   | 10      | 101   | 1     | 0.18   |
| Seagate   | ST3402111A         | 40 GB  | 2       | 117   | 36    | 0.18   |
| Maxtor    | STM3160811AS       | 160 GB | 6       | 687   | 266   | 0.18   |
| WDC       | WD10JPLX-00MBPT0   | 1 TB   | 15      | 70    | 4     | 0.18   |
| Samsung   | SP2014N            | 200 GB | 5       | 362   | 219   | 0.18   |
| WDC       | WD10JUCT-63CYNY0   | 1 TB   | 1       | 66    | 0     | 0.18   |
| WDC       | WD30EZRX-22D8PB0   | 3 TB   | 1       | 65    | 0     | 0.18   |
| WDC       | WD1600AAJS         | 160 GB | 1       | 65    | 0     | 0.18   |
| Hitachi   | HTS545032B9A302    | 320 GB | 2       | 228   | 13    | 0.18   |
| Seagate   | ST3120213A         | 120 GB | 9       | 606   | 708   | 0.18   |
| Toshiba   | MK1011GAH          | 100 GB | 4       | 378   | 9     | 0.18   |
| HGST      | HTS541075A7E630    | 752 GB | 7       | 90    | 145   | 0.17   |
| Seagate   | ST4000DM004-2CV104 | 4 TB   | 13      | 93    | 1     | 0.17   |
| Hitachi   | HTS722080K9A300    | 80 GB  | 2       | 371   | 3     | 0.17   |
| WDC       | WD10EURX-73FH1Y0   | 1 TB   | 2       | 63    | 0     | 0.17   |
| Toshiba   | MK1665GSX          | 160 GB | 14      | 221   | 250   | 0.17   |
| WDC       | WD5000LPVX-16V0TT3 | 500 GB | 2       | 62    | 0     | 0.17   |
| WDC       | WD5000BPKT-80PK4T0 | 500 GB | 1       | 563   | 8     | 0.17   |
| WDC       | WD10EZRX-22L4HB0   | 1 TB   | 1       | 62    | 0     | 0.17   |
| WDC       | WD7500BPVT-35HXZT3 | 752 GB | 1       | 309   | 4     | 0.17   |
| Maxtor    | 4K060H3            | 64 GB  | 1       | 927   | 14    | 0.17   |
| WDC       | WD5000AZLX-08K2TA0 | 500 GB | 11      | 61    | 0     | 0.17   |
| WDC       | WD3200AAJS-08B4A0  | 320 GB | 1       | 677   | 10    | 0.17   |
| Hitachi   | HTS725016A9A362    | 160 GB | 1       | 61    | 0     | 0.17   |
| HGST      | HTS545025A7E330    | 250 GB | 1       | 60    | 0     | 0.17   |
| Seagate   | ST9402115AS        | 40 GB  | 1       | 60    | 0     | 0.17   |
| Fujitsu   | MHV2100AH PL       | 100 GB | 1       | 423   | 6     | 0.17   |
| WDC       | WD10SPZX-22Z10T0   | 1 TB   | 5       | 60    | 0     | 0.17   |
| Hitachi   | DK23FB-60          | 64 GB  | 1       | 960   | 15    | 0.16   |
| WDC       | WD2500AAJS-98B4A0  | 250 GB | 1       | 540   | 8     | 0.16   |
| IBM/Hi... | IC25N080ATMR04-0   | 80 GB  | 3       | 195   | 19    | 0.16   |
| WDC       | WD1600BB-22GUC0    | 160 GB | 1       | 898   | 14    | 0.16   |
| Samsung   | HM120JI            | 120 GB | 4       | 327   | 5     | 0.16   |
| Toshiba   | MK1646GSX          | 160 GB | 6       | 564   | 68    | 0.16   |
| WDC       | WD1600BEVE-00A0HT0 | 160 GB | 1       | 58    | 0     | 0.16   |
| WDC       | WD3200LPVT-22G33T0 | 320 GB | 1       | 58    | 0     | 0.16   |
| WDC       | WD3200AAJS-07M0A0  | 320 GB | 1       | 523   | 8     | 0.16   |
| MediaMax  | WL250GPA872B       | 250 GB | 1       | 58    | 0     | 0.16   |
| WDC       | WD1600AAJS-08L7A0  | 160 GB | 4       | 415   | 317   | 0.16   |
| Seagate   | ST500LM021-1KJ152  | 500 GB | 36      | 93    | 110   | 0.16   |
| Seagate   | ST9250311CS        | 250 GB | 1       | 2074  | 35    | 0.16   |
| Seagate   | ST1000LM014-1EJ... | 1 TB   | 4       | 145   | 1     | 0.16   |
| WDC       | WD10SPZX-24Z10T0   | 1 TB   | 3       | 56    | 0     | 0.16   |
| Seagate   | ST6000NM0115-1Y... | 6 TB   | 3       | 56    | 0     | 0.15   |
| Seagate   | ST2000LM007-1R8174 | 2 TB   | 13      | 59    | 6     | 0.15   |
| WDC       | WD20EZRZ-60Z5HB0   | 2 TB   | 2       | 56    | 0     | 0.15   |
| WDC       | WD3200BEKT-60F3T1  | 320 GB | 4       | 311   | 256   | 0.15   |
| WDC       | WD1002FBYS-01A6B0  | 1 TB   | 1       | 393   | 6     | 0.15   |
| Seagate   | ST3200826A         | 200 GB | 2       | 561   | 8     | 0.15   |
| WDC       | WD2500AAJS-00YZCA0 | 250 GB | 2       | 367   | 4     | 0.15   |
| WDC       | WD1500HLHX-01JJPV0 | 150 GB | 1       | 498   | 8     | 0.15   |
| WDC       | WD10EALX-229BA1    | 1 TB   | 1       | 493   | 8     | 0.15   |
| Seagate   | ST250LT007-9ZV14C  | 250 GB | 1       | 54    | 0     | 0.15   |
| Samsung   | SP1213N            | 120 GB | 3       | 1017  | 346   | 0.15   |
| WDC       | WD10EZEX-35M2NA0   | 1 TB   | 1       | 54    | 0     | 0.15   |
| WDC       | WD1600YS-23SHB0    | 160 GB | 1       | 53    | 0     | 0.15   |
| WDC       | WD360GD-00FLA2     | 37 GB  | 3       | 914   | 19    | 0.15   |
| Hitachi   | HDT725032VLAT80    | 320 GB | 3       | 1450  | 89    | 0.15   |
| WDC       | WD1600BEVS-00RST0  | 160 GB | 1       | 52    | 0     | 0.15   |
| IBM/Hi... | IC25N030ATCS04-0   | 32 GB  | 1       | 52    | 0     | 0.14   |
| WDC       | WD2500BEVT-22ZAT0  | 250 GB | 1       | 316   | 5     | 0.14   |
| WDC       | WD3200BEVT-11ZCT0  | 320 GB | 2       | 60    | 1     | 0.14   |
| Hitachi   | HTS424040M9AT00    | 40 GB  | 6       | 456   | 186   | 0.14   |
| Hitachi   | HTS722010K9SA00    | 100 GB | 1       | 468   | 8     | 0.14   |
| WDC       | WD5000LPLX-21ZNTT0 | 500 GB | 2       | 52    | 0     | 0.14   |
| Toshiba   | MK2552GSX          | 250 GB | 6       | 507   | 43    | 0.14   |
| Toshiba   | MK1629GSG          | 160 GB | 2       | 409   | 9     | 0.14   |
| Seagate   | ST1000LM048-2E7172 | 1 TB   | 25      | 66    | 5     | 0.14   |
| WDC       | WD3200BEVT-60ZCT0  | 320 GB | 5       | 269   | 24    | 0.14   |
| HGST      | HTE721010A9E630    | 1 TB   | 3       | 50    | 0     | 0.14   |
| WDC       | WD1600AAJB-56R1A0  | 160 GB | 2       | 152   | 4     | 0.14   |
| Seagate   | ST960812A          | 64 GB  | 1       | 151   | 2     | 0.14   |
| Seagate   | ST96023AS          | 64 GB  | 1       | 554   | 10    | 0.14   |
| Seagate   | ST2000LX001-1RG174 | 2 TB   | 4       | 223   | 253   | 0.14   |
| Fujitsu   | MJA2250BH G2       | 250 GB | 6       | 253   | 176   | 0.14   |
| WDC       | WD20NPVZ-00WFZT0   | 2 TB   | 1       | 50    | 0     | 0.14   |
| Samsung   | SP1213C            | 120 GB | 5       | 677   | 45    | 0.14   |
| Toshiba   | MK3265GSXF         | 320 GB | 3       | 155   | 5     | 0.14   |
| WDC       | WD5003AZEX-00K3CA0 | 500 GB | 2       | 138   | 4     | 0.13   |
| WDC       | WD1600BEKT-60V5T1  | 160 GB | 2       | 145   | 1     | 0.13   |
| WDC       | WD10JUCT-61CYNY0   | 1 TB   | 1       | 48    | 0     | 0.13   |
| WDC       | WD600UE-22KVT0     | 64 GB  | 1       | 243   | 4     | 0.13   |
| WDC       | WD2500BPVT-26JJ5T0 | 250 GB | 1       | 48    | 0     | 0.13   |
| Seagate   | ST4000NM0035-1V... | 4 TB   | 1       | 48    | 0     | 0.13   |
| Toshiba   | MK1059GSM          | 1 TB   | 18      | 342   | 992   | 0.13   |
| WDC       | WD3200BEVT-22A0RT0 | 320 GB | 3       | 150   | 5     | 0.13   |
| Seagate   | ST9160412AS        | 160 GB | 6       | 534   | 447   | 0.13   |
| WDC       | WD6001FSYZ-01SS7B1 | 6 TB   | 1       | 47    | 0     | 0.13   |
| Hitachi   | HTS542512K9A300    | 120 GB | 3       | 392   | 6     | 0.13   |
| Samsung   | SP1203N            | 120 GB | 6       | 486   | 31    | 0.13   |
| Hitachi   | HTS421210H9AT00    | 100 GB | 1       | 568   | 11    | 0.13   |
| Seagate   | ST10000DM0004-1... | 10 TB  | 1       | 425   | 8     | 0.13   |
| WDC       | WD7500AACS-00D6B1  | 752 GB | 1       | 423   | 8     | 0.13   |
| Toshiba   | MK4055GSX          | 400 GB | 2       | 285   | 3     | 0.13   |
| Seagate   | ST500LM030-2E717D  | 500 GB | 17      | 46    | 0     | 0.13   |
| HGST      | HTS541010B7E610    | 1 TB   | 10      | 46    | 0     | 0.13   |
| Toshiba   | HDWJ105            | 500 GB | 4       | 46    | 0     | 0.13   |
| Hitachi   | HTS541660J9AT00    | 64 GB  | 1       | 184   | 3     | 0.13   |
| WDC       | WD1600BB-00GUC0    | 160 GB | 3       | 769   | 81    | 0.13   |
| HGST      | HTS545050B7E660    | 500 GB | 13      | 45    | 0     | 0.12   |
| Samsung   | SV4012H            | 40 GB  | 2       | 1504  | 236   | 0.12   |
| WDC       | WD10SPZX-00Z10T0   | 1 TB   | 5       | 45    | 0     | 0.12   |
| Seagate   | ST1000LX015-1U7172 | 1 TB   | 11      | 60    | 92    | 0.12   |
| WDC       | WD3200AAJS-00V4A0  | 320 GB | 3       | 396   | 9     | 0.12   |
| Toshiba   | MK3265GSX H        | 320 GB | 1       | 45    | 0     | 0.12   |
| Toshiba   | MQ01ABF050M        | 500 GB | 4       | 44    | 0     | 0.12   |
| ExcelStor | J880S              | 82 GB  | 1       | 44    | 0     | 0.12   |
| Toshiba   | MK6008GAH          | 64 GB  | 2       | 399   | 8     | 0.12   |
| Hitachi   | HTS543225L9SA00    | 250 GB | 4       | 560   | 49    | 0.12   |
| Toshiba   | MK1652GSX          | 160 GB | 12      | 369   | 74    | 0.12   |
| Maxtor    | STM3320613AS       | 320 GB | 10      | 1156  | 283   | 0.12   |
| Seagate   | ST31500341AS       | 1.5 TB | 49      | 784   | 301   | 0.12   |
| Seagate   | ST1000DX002-2DV162 | 1 TB   | 7       | 43    | 0     | 0.12   |
| Hitachi   | HDP725025GLAT80    | 250 GB | 1       | 216   | 4     | 0.12   |
| Toshiba   | MK3276GSX H        | 320 GB | 1       | 43    | 0     | 0.12   |
| Seagate   | ST3750330AS        | 752 GB | 10      | 783   | 357   | 0.12   |
| Seagate   | ST2000VX000-9YW164 | 2 TB   | 7       | 700   | 892   | 0.12   |
| Maxtor    | 6B300R0            | 304 GB | 1       | 42    | 0     | 0.12   |
| WDC       | WD5000AZLX-75K2TA0 | 500 GB | 2       | 42    | 0     | 0.12   |
| WDC       | WD1503FYYS-02W0B0  | 1.5 TB | 1       | 382   | 8     | 0.12   |
| Toshiba   | MK5056GSY          | 500 GB | 2       | 204   | 2     | 0.12   |
| Toshiba   | HDWL110            | 1 TB   | 1       | 42    | 0     | 0.12   |
| WDC       | WD10EZEX-00MFCA0   | 1 TB   | 5       | 42    | 0     | 0.12   |
| IBM/Hi... | IC25N060ATMR04-0   | 64 GB  | 5       | 215   | 10    | 0.11   |
| WDC       | WD15NMVW-11EDZS6   | 1.5 TB | 1       | 41    | 0     | 0.11   |
| WDC       | WD60EZRZ-00GZ5B1   | 6 TB   | 1       | 41    | 0     | 0.11   |
| Hitachi   | HTS545050B9SA00    | 500 GB | 6       | 844   | 842   | 0.11   |
| Maxtor    | 7L250R0            | 256 GB | 1       | 40    | 0     | 0.11   |
| Toshiba   | MK3275GSX          | 320 GB | 11      | 216   | 254   | 0.11   |
| Fujitsu   | MHV2200BT PL       | 200 GB | 1       | 325   | 7     | 0.11   |
| WDC       | WD1600BEVE-00UYT0  | 160 GB | 1       | 40    | 0     | 0.11   |
| WDC       | WD3200LPVT-00G33T0 | 320 GB | 2       | 40    | 0     | 0.11   |
| Maxtor    | 6Y120M0            | 122 GB | 1       | 40    | 0     | 0.11   |
| WDC       | WD30EZRX-00AZ6B0   | 3 TB   | 1       | 40    | 0     | 0.11   |
| WDC       | WD6400AAKS-55A7B2  | 640 GB | 1       | 361   | 8     | 0.11   |
| WDC       | WD1600BEKT-60A25T1 | 160 GB | 1       | 79    | 1     | 0.11   |
| Toshiba   | HDWQ140            | 4 TB   | 2       | 39    | 0     | 0.11   |
| Seagate   | ST1000LM035-1RK172 | 1 TB   | 56      | 48    | 78    | 0.11   |
| MediaMax  | WL1000GSA3254G     | 1 TB   | 1       | 476   | 11    | 0.11   |
| Hitachi   | HTS545012B9SA00    | 120 GB | 1       | 197   | 4     | 0.11   |
| WDC       | WD3200BPVT-00HXZT3 | 320 GB | 3       | 260   | 9     | 0.11   |
| WDC       | WD2000JS-22NCB1    | 200 GB | 1       | 1921  | 48    | 0.11   |
| Seagate   | ST1000NM0008-2F... | 1 TB   | 1       | 39    | 0     | 0.11   |
| WDC       | WD10SPZX-21Z10T0   | 1 TB   | 9       | 39    | 0     | 0.11   |
| WDC       | WD5000AVCS-612DY1  | 500 GB | 1       | 582   | 14    | 0.11   |
| Toshiba   | MK1252GSX          | 120 GB | 6       | 332   | 128   | 0.11   |
| Hitachi   | HTS421280H9AT00    | 80 GB  | 2       | 776   | 30    | 0.11   |
| Samsung   | HM060HI            | 64 GB  | 1       | 541   | 13    | 0.11   |
| WDC       | WD2500AAKS-00F0A0  | 250 GB | 5       | 474   | 58    | 0.11   |
| WDC       | WD10SPCX-21KHST0   | 1 TB   | 2       | 38    | 0     | 0.11   |
| Samsung   | HM100JC            | 100 GB | 1       | 383   | 9     | 0.10   |
| WDC       | WD1500ADFD-00NLR5  | 150 GB | 1       | 344   | 8     | 0.10   |
| Hitachi   | HTS541020G9SA00    | 20 GB  | 1       | 38    | 0     | 0.10   |
| WDC       | WD15EADS-22P8B0    | 1.5 TB | 1       | 339   | 8     | 0.10   |
| Hitachi   | HDT721050SLA380    | 500 GB | 1       | 224   | 5     | 0.10   |
| Seagate   | ST500LM030-1RK17D  | 500 GB | 5       | 37    | 0     | 0.10   |
| WDC       | WD3200BEVS-16VAT0  | 320 GB | 1       | 37    | 0     | 0.10   |
| HGST      | HTS541515A9E630    | 1.5 TB | 2       | 541   | 14    | 0.10   |
| WDC       | WD1002FBYS-18W8B0  | 1 TB   | 1       | 36    | 0     | 0.10   |
| WDC       | WD5000BEVT-80A0RT1 | 500 GB | 2       | 284   | 7     | 0.10   |
| Hitachi   | HTS543212L9A300    | 120 GB | 2       | 232   | 72    | 0.10   |
| WDC       | WD800AAJS-60B4A0   | 80 GB  | 2       | 1529  | 24    | 0.10   |
| WDC       | WD2500AAJS-75B4A0  | 250 GB | 2       | 348   | 9     | 0.10   |
| Toshiba   | MK2046GSX          | 200 GB | 9       | 408   | 51    | 0.10   |
| Maxtor    | 6L120P0            | 122 GB | 2       | 35    | 0     | 0.10   |
| WDC       | WD30EZRS-00J99B0   | 3 TB   | 4       | 801   | 875   | 0.10   |
| Toshiba   | MQ01UBD050         | 500 GB | 1       | 35    | 0     | 0.10   |
| Toshiba   | MQ04ABF100         | 1 TB   | 13      | 34    | 0     | 0.10   |
| Samsung   | HM320JI            | 320 GB | 4       | 419   | 10    | 0.10   |
| WDC       | WD1200BEVS-07LAT0  | 120 GB | 4       | 373   | 249   | 0.10   |
| Hitachi   | HTS725025A9A361... | 250 GB | 1       | 34    | 0     | 0.09   |
| Toshiba   | MK5055GSX          | 500 GB | 7       | 553   | 200   | 0.09   |
| WDC       | WD5000BEKT-22KA9T0 | 500 GB | 1       | 302   | 8     | 0.09   |
| Hitachi   | HDS722580VLAT20    | 82 GB  | 3       | 418   | 180   | 0.09   |
| HGST      | HTS541050A9E680    | 500 GB | 3       | 33    | 0     | 0.09   |
| WDC       | WD1600BB-55GUA0    | 160 GB | 1       | 668   | 19    | 0.09   |
| Maxtor    | 2F030L0            | 30 GB  | 1       | 33    | 0     | 0.09   |
| Toshiba   | HDWM105            | 500 GB | 1       | 32    | 0     | 0.09   |
| WDC       | WD10JPVX-08JC3T6   | 1 TB   | 2       | 32    | 0     | 0.09   |
| Maxtor    | 6L200P0            | 208 GB | 2       | 32    | 0     | 0.09   |
| Seagate   | ST1000VM002-1ET162 | 1 TB   | 1       | 32    | 0     | 0.09   |
| MicroData | MD1TBLSSHD         | 1 TB   | 1       | 288   | 8     | 0.09   |
| WDC       | WD5000LPLX-60ZNTT1 | 500 GB | 7       | 81    | 40    | 0.09   |
| WDC       | WD10E              | 1 TB   | 1       | 31    | 0     | 0.09   |
| HGST      | HUS726020ALE614    | 2 TB   | 1       | 31    | 0     | 0.09   |
| WDC       | WD10JPVT-00A1YT0   | 1 TB   | 1       | 31    | 0     | 0.09   |
| WDC       | WD1600BEVS-00VAT0  | 160 GB | 1       | 31    | 0     | 0.09   |
| Toshiba   | MQ03UBB300         | 3 TB   | 2       | 35    | 4     | 0.09   |
| WDC       | WD800JB-00FSA0     | 80 GB  | 1       | 1366  | 43    | 0.09   |
| WDC       | WD2500JD-00HBC0    | 250 GB | 1       | 620   | 19    | 0.09   |
| Maxtor    | 2F030J1            | 30 GB  | 1       | 185   | 5     | 0.08   |
| WDC       | WD5000AAJS-00YFA0  | 500 GB | 2       | 469   | 81    | 0.08   |
| WDC       | WD20EVDS-63T3B0    | 2 TB   | 1       | 273   | 8     | 0.08   |
| Seagate   | ST38410A           | 8 GB   | 1       | 754   | 24    | 0.08   |
| Seagate   | ST3500320AS        | 500 GB | 64      | 824   | 511   | 0.08   |
| WDC       | WD40EZRZ-00GXCB0   | 4 TB   | 2       | 29    | 0     | 0.08   |
| WDC       | WD600VE-75HDT0     | 64 GB  | 1       | 268   | 8     | 0.08   |
| Samsung   | SV0401N            | 40 GB  | 1       | 952   | 31    | 0.08   |
| Seagate   | ST750LM028-1KK162  | 752 GB | 1       | 29    | 0     | 0.08   |
| WDC       | WD5000AZLX-22JKKA0 | 500 GB | 6       | 29    | 0     | 0.08   |
| Samsung   | MP0804H            | 80 GB  | 3       | 243   | 8     | 0.08   |
| WDC       | WD1600JS-00MHB1    | 160 GB | 1       | 1060  | 35    | 0.08   |
| Samsung   | SV0412H            | 40 GB  | 4       | 957   | 88    | 0.08   |
| WDC       | WD5000AAKX-00KJ3A0 | 500 GB | 1       | 262   | 8     | 0.08   |
| Hitachi   | HTS421260H9AT00    | 64 GB  | 2       | 241   | 10    | 0.08   |
| WDC       | WD2004FBYZ-01YCBB1 | 2 TB   | 4       | 29    | 0     | 0.08   |
| WDC       | WD3200JB-00KFA0    | 320 GB | 1       | 29    | 0     | 0.08   |
| Seagate   | ST3640323AS        | 640 GB | 7       | 1126  | 533   | 0.08   |
| Maxtor    | 6L080M0            | 80 GB  | 3       | 28    | 0     | 0.08   |
| Seagate   | ST500LM034-2GH17A  | 500 GB | 1       | 28    | 0     | 0.08   |
| Seagate   | ST500DM009-2F110A  | 500 GB | 8       | 46    | 4     | 0.08   |
| Hitachi   | HTS543212L9SA02    | 120 GB | 1       | 27    | 0     | 0.08   |
| Toshiba   | MQ01ABD100M        | 1 TB   | 1       | 27    | 0     | 0.08   |
| MARSHAL   | MAL2500SA-T54      | 500 GB | 1       | 279   | 9     | 0.08   |
| Hitachi   | HTS541040G9SA00    | 40 GB  | 1       | 415   | 14    | 0.08   |
| WDC       | WD2000JD-55HBC0    | 200 GB | 1       | 26    | 0     | 0.07   |
| WDC       | WD3200AVVS-63L2B0  | 320 GB | 3       | 56    | 4     | 0.07   |
| WDC       | WD2502ABYS-02B7A0  | 256 GB | 1       | 316   | 11    | 0.07   |
| WDC       | WD3200AAJS-00VWA1  | 320 GB | 1       | 708   | 26    | 0.07   |
| Hitachi   | HTS548040M9AT00    | 40 GB  | 1       | 470   | 17    | 0.07   |
| Seagate   | ST9250320AS        | 250 GB | 14      | 287   | 254   | 0.07   |
| WDC       | WD30NMVW-11C3NS2   | 3 TB   | 1       | 25    | 0     | 0.07   |
| WDC       | WD80EMAZ-00WJTA0   | 8 TB   | 1       | 25    | 0     | 0.07   |
| WDC       | WD15EADS-00S2B0    | 1.5 TB | 1       | 483   | 18    | 0.07   |
| Fujitsu   | MHT2080BH          | 80 GB  | 1       | 403   | 15    | 0.07   |
| Toshiba   | MK5059GSX          | 500 GB | 1       | 932   | 36    | 0.07   |
| Seagate   | ST500LM016 HN-M... | 500 GB | 1       | 24    | 0     | 0.07   |
| WDC       | WD40EZRZ-75GXCB0   | 4 TB   | 4       | 24    | 0     | 0.07   |
| Seagate   | ST3250310CS        | 250 GB | 1       | 1067  | 42    | 0.07   |
| WDC       | WD6400BEVT-80A0RT1 | 640 GB | 1       | 664   | 26    | 0.07   |
| Hitachi   | HTS725032A9A360    | 320 GB | 1       | 24    | 0     | 0.07   |
| WDC       | WD2500AAJS-52B4A0  | 250 GB | 2       | 942   | 45    | 0.07   |
| Toshiba   | HDWK105            | 500 GB | 2       | 24    | 0     | 0.07   |
| Samsung   | HM160HC            | 160 GB | 6       | 187   | 23    | 0.07   |
| Maxtor    | STM3500320AS       | 500 GB | 12      | 717   | 388   | 0.07   |
| WDC       | WD10SPCX-75KHST0   | 1 TB   | 1       | 24    | 0     | 0.07   |
| WDC       | WD400VE-75HDT1     | 40 GB  | 1       | 23    | 0     | 0.06   |
| Samsung   | HD160HJ            | 160 GB | 13      | 552   | 732   | 0.06   |
| Apple     | HDD HTS547550A9... | 500 GB | 1       | 23    | 0     | 0.06   |
| Toshiba   | MK6032GAX          | 64 GB  | 1       | 23    | 0     | 0.06   |
| Seagate   | ST4000VX000-2AG166 | 4 TB   | 1       | 23    | 0     | 0.06   |
| WDC       | WD2500BEVT-60A23T0 | 250 GB | 3       | 258   | 27    | 0.06   |
| Toshiba   | MK6465GSXW         | 640 GB | 1       | 552   | 23    | 0.06   |
| Toshiba   | MK2529GSG          | 250 GB | 2       | 313   | 1127  | 0.06   |
| WDC       | WD10SMZW-11Y0TS0   | 1 TB   | 3       | 22    | 0     | 0.06   |
| WDC       | WD3200AUDX-56WNHY0 | 320 GB | 1       | 22    | 0     | 0.06   |
| WDC       | WD2000JS-60NCB1    | 200 GB | 2       | 192   | 6     | 0.06   |
| Samsung   | HM251JI            | 250 GB | 6       | 334   | 527   | 0.06   |
| Toshiba   | MK1032GAX          | 100 GB | 2       | 108   | 4     | 0.06   |
| WDC       | WD3200BEKX-22B7WT0 | 320 GB | 1       | 21    | 0     | 0.06   |
| Seagate   | ST2000VM003-1ET164 | 2 TB   | 1       | 21    | 0     | 0.06   |
| Seagate   | ST3300831A         | 304 GB | 1       | 347   | 15    | 0.06   |
| Seagate   | ST3250824SCE       | 250 GB | 1       | 21    | 0     | 0.06   |
| Hitachi   | HTS722016K9A300    | 160 GB | 1       | 236   | 10    | 0.06   |
| WDC       | WD5000AVDS-73U7B1  | 500 GB | 2       | 189   | 7     | 0.06   |
| WDC       | WD3200BVVT-63A26Y0 | 320 GB | 1       | 42    | 1     | 0.06   |
| WDC       | WD5000LPCX-75VHAT0 | 500 GB | 7       | 21    | 0     | 0.06   |
| Hitachi   | HTS721060G9SA00    | 64 GB  | 2       | 335   | 17    | 0.06   |
| Maxtor    | STM3160613AS       | 160 GB | 1       | 41    | 1     | 0.06   |
| Fujitsu   | MHT2040AT          | 40 GB  | 1       | 166   | 7     | 0.06   |
| WDC       | WD400BB-22DEA0     | 40 GB  | 1       | 831   | 39    | 0.06   |
| Samsung   | HM160HI            | 160 GB | 46      | 364   | 345   | 0.06   |
| WDC       | WD2000BB-00GUC0    | 200 GB | 1       | 637   | 30    | 0.06   |
| Maxtor    | 6B200M0            | 200 GB | 3       | 26    | 13    | 0.06   |
| WDC       | WD5000BPVT-75A1YT0 | 500 GB | 1       | 20    | 0     | 0.06   |
| WDC       | WD2500BPVT-00ZEST0 | 250 GB | 3       | 136   | 74    | 0.06   |
| Seagate   | ST1000LM010-9YH146 | 1 TB   | 7       | 110   | 1022  | 0.06   |
| WDC       | WD5000AZLX-60K2TA0 | 500 GB | 3       | 20    | 0     | 0.05   |
| WDC       | WD2500LPCX-24VHAT0 | 250 GB | 2       | 55    | 5     | 0.05   |
| IBM       | DARA-206000        | 6 GB   | 1       | 118   | 5     | 0.05   |
| Seagate   | ST3160215SCE       | 160 GB | 1       | 98    | 4     | 0.05   |
| Seagate   | ST9250610NS        | 250 GB | 2       | 19    | 0     | 0.05   |
| IBM/Hi... | IC25N040ATMR04-0   | 40 GB  | 2       | 628   | 181   | 0.05   |
| WDC       | WD200EB-75CPF0     | 20 GB  | 2       | 402   | 20    | 0.05   |
| WDC       | WD1600JD-00GBB0    | 160 GB | 1       | 727   | 37    | 0.05   |
| Seagate   | ST31000340AS       | 1 TB   | 6       | 1025  | 364   | 0.05   |
| Samsung   | HM080HI            | 80 GB  | 2       | 473   | 405   | 0.05   |
| Toshiba   | MK5076GSX          | 500 GB | 25      | 52    | 192   | 0.05   |
| WDC       | WD5000LPVX-16V0TT0 | 500 GB | 1       | 71    | 3     | 0.05   |
| Quantum   | FIREBALLlct15 10   | 10 GB  | 1       | 105   | 5     | 0.05   |
| Seagate   | ST31000340NS       | 1 TB   | 9       | 1183  | 456   | 0.05   |
| Samsung   | HM121HC            | 120 GB | 2       | 179   | 26    | 0.05   |
| WDC       | WD2500JS-75NCB1    | 250 GB | 1       | 2681  | 153   | 0.05   |
| WDC       | WD1600JS-55MHB0    | 160 GB | 1       | 761   | 43    | 0.05   |
| Hitachi   | HDP725032GLAT80    | 320 GB | 1       | 943   | 55    | 0.05   |
| Seagate   | ST3320310CS        | 320 GB | 3       | 576   | 32    | 0.05   |
| Fujitsu   | MHZ2320BH G2       | 320 GB | 6       | 499   | 453   | 0.04   |
| Samsung   | HN-M250MBB         | 250 GB | 1       | 292   | 17    | 0.04   |
| Maxtor    | 2F040L0            | 41 GB  | 3       | 25    | 2     | 0.04   |
| WDC       | WD800BB-88JHC0     | 80 GB  | 1       | 1625  | 101   | 0.04   |
| Hitachi   | HDT721050SLA360    | 500 GB | 2       | 1337  | 95    | 0.04   |
| Hitachi   | HTS545025A7E380    | 250 GB | 1       | 15    | 0     | 0.04   |
| IBM/Hi... | IC35L060AVVA07-0   | 61 GB  | 1       | 678   | 42    | 0.04   |
| WDC       | WD5000LPLX-66ZNTT1 | 500 GB | 1       | 31    | 1     | 0.04   |
| HGST      | HUS722T1TALA604    | 1 TB   | 3       | 15    | 0     | 0.04   |
| Maxtor    | STM3160813AS       | 160 GB | 4       | 793   | 543   | 0.04   |
| Seagate   | ST500VM000-1SD101  | 500 GB | 1       | 15    | 0     | 0.04   |
| WDC       | WD4000ABYS-01TNA0  | 400 GB | 1       | 688   | 44    | 0.04   |
| Samsung   | SP1253N            | 120 GB | 1       | 286   | 18    | 0.04   |
| Toshiba   | MK6034GSX          | 64 GB  | 3       | 320   | 23    | 0.04   |
| Seagate   | ST1000LM049-2GH172 | 1 TB   | 13      | 14    | 0     | 0.04   |
| Hitachi   | HTS543232L9SA02    | 320 GB | 1       | 1255  | 84    | 0.04   |
| Samsung   | SP1614C            | 160 GB | 2       | 124   | 22    | 0.04   |
| Hitachi   | HTS723225L9A360    | 250 GB | 3       | 322   | 1301  | 0.04   |
| Seagate   | OOS500G            | 500 GB | 1       | 14    | 0     | 0.04   |
| Seagate   | ST9120310AS        | 120 GB | 1       | 14    | 0     | 0.04   |
| WDC       | WD10EADS-11M2B1    | 1 TB   | 1       | 526   | 37    | 0.04   |
| Seagate   | ST91000640NS       | 1 TB   | 1       | 13    | 0     | 0.04   |
| WDC       | WD20NPVT-00Z2TT0   | 2 TB   | 2       | 191   | 18    | 0.04   |
| Seagate   | ST310212A          | 10 GB  | 1       | 380   | 27    | 0.04   |
| Toshiba   | MK2565GSXN         | 250 GB | 1       | 502   | 36    | 0.04   |
| WDC       | WD10SPZX-24Z10     | 1 TB   | 3       | 13    | 0     | 0.04   |
| WDC       | WD5000AADS-98S9B1  | 500 GB | 1       | 120   | 8     | 0.04   |
| WDC       | WD3200AAJS-00RYA0  | 320 GB | 2       | 1320  | 143   | 0.03   |
| Fujitsu   | MPG3204AT E        | 20 GB  | 1       | 138   | 10    | 0.03   |
| Seagate   | ST3250412CS        | 250 GB | 1       | 12    | 0     | 0.03   |
| Maxtor    | 6L160P0            | 163 GB | 4       | 32    | 6     | 0.03   |
| Toshiba   | MK2565GSXV         | 250 GB | 2       | 275   | 34    | 0.03   |
| WDC       | WD2500JS-75NCB3    | 250 GB | 1       | 1194  | 98    | 0.03   |
| Seagate   | ST31000333AS       | 1 TB   | 18      | 688   | 490   | 0.03   |
| Maxtor    | 6L160M0            | 160 GB | 5       | 23    | 421   | 0.03   |
| WDC       | WD7500LPCX-22HWST0 | 752 GB | 1       | 129   | 10    | 0.03   |
| WDC       | WD2500AAJS-60M0A0  | 250 GB | 2       | 705   | 533   | 0.03   |
| Samsung   | HM502JX            | 500 GB | 1       | 11    | 0     | 0.03   |
| WDC       | WD10SPZX-60Z10T0   | 1 TB   | 6       | 11    | 0     | 0.03   |
| IBM/Hi... | IC35L060AVV207-0   | 40 GB  | 1       | 325   | 27    | 0.03   |
| WDC       | WD800BB-00CAA0     | 80 GB  | 1       | 414   | 35    | 0.03   |
| Maxtor    | 2F030J0            | 30 GB  | 2       | 33    | 2     | 0.03   |
| Hitachi   | HDS722525VLAT80    | 250 GB | 1       | 11    | 0     | 0.03   |
| Toshiba   | HDWM110            | 1 TB   | 2       | 11    | 0     | 0.03   |
| Maxtor    | STM3320820A        | 320 GB | 1       | 11    | 0     | 0.03   |
| WDC       | WD5000AAKS-19V0A0  | 500 GB | 1       | 1131  | 103   | 0.03   |
| Toshiba   | MK1656GSY          | 160 GB | 2       | 190   | 9     | 0.03   |
| Seagate   | STM31000528AS      | 1 TB   | 2       | 10    | 0     | 0.03   |
| Hitachi   | HTS541660J9SA00    | 64 GB  | 2       | 112   | 12    | 0.03   |
| WDC       | WD7500BPVT-60HXZT1 | 752 GB | 2       | 815   | 84    | 0.03   |
| WDC       | WD1002FBYS-43P1B0  | 1 TB   | 1       | 783   | 77    | 0.03   |
| WDC       | WD5000LPCX-75VHAT1 | 500 GB | 2       | 9     | 0     | 0.03   |
| Fujitsu   | MHV2120BH PL       | 120 GB | 8       | 28    | 3     | 0.03   |
| Toshiba   | MK2016GAP          | 20 GB  | 1       | 349   | 36    | 0.03   |
| Seagate   | ST9808210A         | 80 GB  | 1       | 344   | 37    | 0.02   |
| WDC       | WD3200AAJS-40VWA1  | 320 GB | 1       | 375   | 41    | 0.02   |
| Maxtor    | 6E040L0            | 40 GB  | 8       | 29    | 35    | 0.02   |
| Maxtor    | 4K040H2            | 33 GB  | 1       | 298   | 33    | 0.02   |
| WDC       | WD10EZRX-00A3KB0   | 1 TB   | 1       | 8     | 0     | 0.02   |
| WDC       | WD3200BEVT-80A0RT1 | 320 GB | 2       | 1035  | 140   | 0.02   |
| WDC       | WD2500JS-60MHB1    | 250 GB | 1       | 124   | 14    | 0.02   |
| Maxtor    | 6Y120L0            | 122 GB | 6       | 29    | 16    | 0.02   |
| Hitachi   | HTS548080M9AT00    | 80 GB  | 1       | 136   | 16    | 0.02   |
| ExcelStor | J9250              | 250 GB | 1       | 1349  | 167   | 0.02   |
| MediaMax  | WL250GLSA6410000   | 250 GB | 2       | 36    | 4     | 0.02   |
| Seagate   | ST9320421AS        | 320 GB | 2       | 709   | 98    | 0.02   |
| LENOVO    | WD1004FBYZ-23YC... | 1 TB   | 2       | 7     | 0     | 0.02   |
| Hitachi   | HUS724030ALE641    | 3 TB   | 1       | 7     | 0     | 0.02   |
| WDC       | WD5000LPCX-08VHA   | 500 GB | 5       | 7     | 0     | 0.02   |
| Maxtor    | 6Y060L2            | 61 GB  | 1       | 542   | 71    | 0.02   |
| Maxtor    | 6K040L0            | 41 GB  | 1       | 29    | 3     | 0.02   |
| WDC       | WD40EZRZ-22GXCB0   | 4 TB   | 1       | 7     | 0     | 0.02   |
| Hitachi   | HTS723232L9A360    | 320 GB | 3       | 983   | 718   | 0.02   |
| Hitachi   | DK23EA-20B         | 17 GB  | 1       | 183   | 24    | 0.02   |
| WDC       | WD20PURZ-85GU6Y0   | 2 TB   | 2       | 7     | 0     | 0.02   |
| WDC       | WD2000JS-00NCB1    | 200 GB | 1       | 537   | 73    | 0.02   |
| WDC       | WD3200BEKT-75PVMT0 | 320 GB | 1       | 208   | 28    | 0.02   |
| HP        | GB0250C8045        | 250 GB | 1       | 1405  | 198   | 0.02   |
| WDC       | WD5000LPCX-22VHAT1 | 500 GB | 2       | 6     | 0     | 0.02   |
| WDC       | WD3200KS-75PFB0    | 320 GB | 1       | 550   | 78    | 0.02   |
| Maxtor    | 6E030L0            | 30 GB  | 5       | 15    | 19    | 0.02   |
| WDC       | WD2500AAJS-41RYA0  | 250 GB | 1       | 76    | 10    | 0.02   |
| Maxtor    | 6B250S0            | 250 GB | 1       | 6     | 0     | 0.02   |
| Samsung   | SP1614N            | 160 GB | 1       | 690   | 106   | 0.02   |
| WDC       | WD360ADFD-00NLR4   | 37 GB  | 1       | 499   | 77    | 0.02   |
| Samsung   | HM121HI            | 120 GB | 8       | 460   | 1255  | 0.02   |
| Toshiba   | MQ01ACF032         | 320 GB | 1       | 6     | 0     | 0.02   |
| Maxtor    | 6L120M0            | 122 GB | 1       | 43    | 6     | 0.02   |
| Maxtor    | 6L080P0            | 81 GB  | 2       | 10    | 10    | 0.02   |
| Toshiba   | MK1214GAH          | 120 GB | 2       | 28    | 209   | 0.02   |
| Seagate   | ST500LT012-9WS142  | 500 GB | 148     | 289   | 1071  | 0.02   |
| Samsung   | HM100JI            | 100 GB | 1       | 827   | 140   | 0.02   |
| Hitachi   | HTS541612J9AT00    | 120 GB | 1       | 116   | 19    | 0.02   |
| Seagate   | ST3500320SV        | 500 GB | 1       | 45    | 7     | 0.02   |
| Toshiba   | MK8052GSX          | 80 GB  | 3       | 180   | 58    | 0.02   |
| Seagate   | ST3000VX010-2E3166 | 3 TB   | 1       | 5     | 0     | 0.01   |
| Toshiba   | MQ02ABF050H-SSH... | 500 GB | 1       | 5     | 0     | 0.01   |
| Seagate   | ST1000LM002-9VQ14L | 1 TB   | 1       | 25    | 4     | 0.01   |
| Maxtor    | 6L080L0            | 81 GB  | 2       | 13    | 3     | 0.01   |
| WDC       | WD15EARS-22MVWB0   | 1.5 TB | 3       | 818   | 514   | 0.01   |
| WDC       | WD1200AAJS-00VTA0  | 120 GB | 1       | 995   | 203   | 0.01   |
| Maxtor    | 6Y080M0            | 80 GB  | 6       | 32    | 39    | 0.01   |
| Hitachi   | HTE721060G9AT00    | 64 GB  | 1       | 4     | 0     | 0.01   |
| Toshiba   | MK2576GSX          | 250 GB | 1       | 4     | 0     | 0.01   |
| WDC       | WD10TMVV-11BG7S0   | 1 TB   | 1       | 27    | 5     | 0.01   |
| Toshiba   | MK5061GSYN         | 500 GB | 11      | 103   | 278   | 0.01   |
| Maxtor    | 4R060J0            | 61 GB  | 1       | 25    | 5     | 0.01   |
| Toshiba   | MK7559GSXF         | 752 GB | 2       | 117   | 637   | 0.01   |
| WDC       | WD3200BEVT-75ZCT0  | 320 GB | 1       | 709   | 167   | 0.01   |
| Seagate   | ST320LT012-9WS14C  | 320 GB | 42      | 214   | 975   | 0.01   |
| Fujitsu   | MHZ2160BJ G1       | 160 GB | 1       | 4     | 0     | 0.01   |
| Maxtor    | 6Y120P0            | 122 GB | 2       | 23    | 8     | 0.01   |
| WDC       | WD800JD-55JRC0     | 80 GB  | 1       | 243   | 62    | 0.01   |
| Samsung   | HM500LI            | 500 GB | 1       | 7     | 1     | 0.01   |
| Maxtor    | 6Y200P0            | 208 GB | 1       | 30    | 7     | 0.01   |
| WDC       | WD2500BEKT-66F3T2  | 250 GB | 1       | 193   | 50    | 0.01   |
| Seagate   | ST2000DM009-2G4100 | 2 TB   | 2       | 3     | 0     | 0.01   |
| Samsung   | HM160JI            | 160 GB | 3       | 605   | 748   | 0.01   |
| Seagate   | ST2000DM008-2FR102 | 2 TB   | 4       | 3     | 0     | 0.01   |
| Maxtor    | 6L300S0            | 304 GB | 3       | 21    | 609   | 0.01   |
| Hitachi   | HTS722012K9A300    | 120 GB | 1       | 781   | 214   | 0.01   |
| Maxtor    | 6L200M0            | 208 GB | 1       | 14    | 3     | 0.01   |
| Seagate   | ST3250310SV        | 250 GB | 1       | 287   | 79    | 0.01   |
| WDC       | WD5000AVJS-63TRA0  | 500 GB | 1       | 2013  | 578   | 0.01   |
| Hitachi   | HTS541640J9AT00    | 40 GB  | 1       | 283   | 82    | 0.01   |
| Maxtor    | 6B200P0            | 208 GB | 1       | 43    | 12    | 0.01   |
| WDC       | WD10EADS-00R6B0    | 1 TB   | 1       | 1856  | 560   | 0.01   |
| Fujitsu   | MPE3136AT          | 13 GB  | 1       | 794   | 240   | 0.01   |
| Apple     | HDD HTS547575A9... | 752 GB | 1       | 506   | 153   | 0.01   |
| IBM/Hi... | IC35L060AVER07-0   | 61 GB  | 1       | 997   | 304   | 0.01   |
| Maxtor    | 2F020J0            | 20 GB  | 1       | 41    | 12    | 0.01   |
| Maxtor    | 6Y080P0            | 81 GB  | 7       | 16    | 7     | 0.01   |
| Maxtor    | 6E020L0            | 20 GB  | 1       | 22    | 6     | 0.01   |
| Seagate   | ST3500620AS        | 500 GB | 2       | 429   | 996   | 0.01   |
| WDC       | WD2004FBYZ-01YCBB0 | 2 TB   | 1       | 12    | 3     | 0.01   |
| Seagate   | ST3320820A         | 320 GB | 1       | 641   | 210   | 0.01   |
| Maxtor    | 6B160M0            | 163 GB | 1       | 3     | 0     | 0.01   |
| Seagate   | ST3500820AS        | 500 GB | 3       | 187   | 61    | 0.01   |
| WDC       | WD10SPZX-75Z10T2   | 1 TB   | 1       | 2     | 0     | 0.01   |
| Seagate   | ST500LM020-1G1162  | 500 GB | 3       | 2     | 0     | 0.01   |
| Maxtor    | 7L250S0            | 250 GB | 1       | 7     | 2     | 0.01   |
| Samsung   | SV0802N            | 80 GB  | 1       | 554   | 215   | 0.01   |
| Seagate   | ST1000VX005-2EZ102 | 1 TB   | 1       | 2     | 0     | 0.01   |
| Seagate   | ST3160212SCE       | 160 GB | 1       | 2510  | 1028  | 0.01   |
| WDC       | WD3200AADS-00S9B0  | 320 GB | 1       | 26    | 10    | 0.01   |
| Toshiba   | MK6459GSX          | 640 GB | 4       | 481   | 839   | 0.01   |
| Maxtor    | 2B020H1            | 20 GB  | 6       | 23    | 75    | 0.01   |
| WDC       | WD5000LPCX-60VHAT1 | 500 GB | 1       | 2     | 0     | 0.01   |
| Toshiba   | MK3259GSX          | 320 GB | 1       | 192   | 82    | 0.01   |
| WDC       | WD2500BEVT-35ZCT0  | 250 GB | 1       | 949   | 450   | 0.01   |
| Hitachi   | HDS722516VLAT20    | 164 GB | 1       | 2242  | 1102  | 0.01   |
| Toshiba   | MK6476GSX          | 640 GB | 11      | 6     | 202   | 0.01   |
| WDC       | WD6400AAKS-00E4A0  | 640 GB | 1       | 1016  | 521   | 0.01   |
| WDC       | WD10EURX-63UHWY0   | 1 TB   | 1       | 644   | 338   | 0.01   |
| WDC       | WD4000AAKS-22TMA0  | 400 GB | 1       | 820   | 431   | 0.01   |
| Toshiba   | MK3276GSX          | 320 GB | 18      | 6     | 225   | 0.01   |
| Seagate   | ST9320423ASG       | 320 GB | 1       | 270   | 145   | 0.01   |
| Maxtor    | 6Y160P0            | 163 GB | 3       | 16    | 193   | 0.01   |
| WDC       | WD10TPVT-00U4RT1   | 1 TB   | 1       | 852   | 463   | 0.01   |
| Toshiba   | MQ02ABF100         | 1 TB   | 1       | 1     | 0     | 0.01   |
| Toshiba   | MK2556GSY          | 250 GB | 3       | 6     | 352   | 0.00   |
| WDC       | WD20EARS-19MVWB0   | 2 TB   | 1       | 713   | 392   | 0.00   |
| Toshiba   | MK2533GSG          | 250 GB | 1       | 1671  | 948   | 0.00   |
| Hitachi   | HTS723216L9A360    | 160 GB | 3       | 454   | 1491  | 0.00   |
| Hitachi   | HUA5C3020ALA640    | 2 TB   | 1       | 1045  | 595   | 0.00   |
| CLOVER    | CD155UI            | 1.5 TB | 1       | 1     | 0     | 0.00   |
| Toshiba   | MK3261GSYN         | 320 GB | 5       | 7     | 169   | 0.00   |
| Maxtor    | 6L250S0            | 250 GB | 1       | 40    | 23    | 0.00   |
| IBM/Hi... | IC35L120AVVA07-0   | 128 GB | 1       | 918   | 552   | 0.00   |
| Seagate   | ST3750630AS        | 752 GB | 1       | 1122  | 686   | 0.00   |
| Maxtor    | 6Y080L0            | 80 GB  | 30      | 20    | 354   | 0.00   |
| Samsung   | HD251KJ            | 250 GB | 1       | 1539  | 1019  | 0.00   |
| Seagate   | ST3120023AS        | 120 GB | 1       | 152   | 101   | 0.00   |
| Toshiba   | MK5065GSXN         | 500 GB | 6       | 521   | 976   | 0.00   |
| Seagate   | ST500VT000-1BS142  | 500 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WD2500JD-98GBB0    | 250 GB | 1       | 875   | 628   | 0.00   |
| Maxtor    | 4D040H2            | 40 GB  | 3       | 18    | 237   | 0.00   |
| WDC       | WD10SPZX-08Z10     | 1 TB   | 1       | 1     | 0     | 0.00   |
| WDC       | WD5000BPVT-60HXZT1 | 500 GB | 1       | 1329  | 1007  | 0.00   |
| WDC       | WD3200LPCX-60VHAT0 | 320 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WD1200             | 120 GB | 1       | 11    | 8     | 0.00   |
| Toshiba   | MK7559GSM          | 752 GB | 1       | 1015  | 847   | 0.00   |
| WDC       | WD30EZRS-11J99B1   | 3 TB   | 1       | 794   | 663   | 0.00   |
| WDC       | WD400BB-00CAA0     | 40 GB  | 1       | 194   | 163   | 0.00   |
| Maxtor    | 4R120L0            | 122 GB | 2       | 43    | 39    | 0.00   |
| Maxtor    | 7Y250M0            | 250 GB | 1       | 43    | 37    | 0.00   |
| WDC       | WD800UE-22HCT0     | 80 GB  | 1       | 436   | 395   | 0.00   |
| WDC       | WD7500AACS-00ZJB0  | 752 GB | 1       | 1106  | 1007  | 0.00   |
| Toshiba   | MK5061GSY          | 500 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WD3200JS-63PDB1    | 320 GB | 1       | 343   | 342   | 0.00   |
| Seagate   | ST3250824A         | 250 GB | 1       | 978   | 1007  | 0.00   |
| Maxtor    | 6Y060L0            | 61 GB  | 4       | 24    | 63    | 0.00   |
| WDC       | WD2500AVVS-62L2B0  | 250 GB | 1       | 9     | 9     | 0.00   |
| Fujitsu   | MHV2160BT          | 160 GB | 1       | 483   | 535   | 0.00   |
| HGST      | TPH00100500GB 0... | 500 GB | 1       | 8     | 10    | 0.00   |
| Toshiba   | MK3256GSY          | 320 GB | 4       | 5     | 282   | 0.00   |
| Maxtor    | STM3750330AS       | 752 GB | 1       | 995   | 1293  | 0.00   |
| MediaMax  | WL400GSA6454G      | 400 GB | 1       | 0     | 0     | 0.00   |
| Seagate   | ST1000VN002-2EY102 | 1 TB   | 1       | 0     | 0     | 0.00   |
| WDC       | WD3200LPCX-22VHAT0 | 320 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD5000BPVX-00JC3T0 | 500 GB | 1       | 0     | 0     | 0.00   |
| Maxtor    | 6Y160M0            | 160 GB | 4       | 16    | 183   | 0.00   |
| HGST      | HTS725050B7E630    | 500 GB | 2       | 0     | 0     | 0.00   |
| WDC       | WD3200BEVS-08VAT2  | 320 GB | 1       | 785   | 1119  | 0.00   |
| Seagate   | ST3320620SV        | 320 GB | 1       | 564   | 835   | 0.00   |
| Fujitsu   | MHZ2120BH G2       | 120 GB | 1       | 693   | 1028  | 0.00   |
| WDC       | WD10EZRZ-22HTKB0   | 1 TB   | 1       | 0     | 0     | 0.00   |
| WDC       | WD800AAJS-60PSA0   | 80 GB  | 1       | 624   | 1007  | 0.00   |
| Hitachi   | DK23EA-40          | 40 GB  | 1       | 287   | 470   | 0.00   |
| Maxtor    | 4D060H3            | 64 GB  | 1       | 18    | 31    | 0.00   |
| WDC       | WD6400BPVT-24HXZT1 | 640 GB | 1       | 560   | 1013  | 0.00   |
| Hitachi   | HUA722010CLA630    | 1 TB   | 1       | 0     | 0     | 0.00   |
| WDC       | WD15EARS-19MVWB0   | 1.5 TB | 1       | 696   | 1306  | 0.00   |
| Hitachi   | HTS723212L9A360    | 120 GB | 1       | 535   | 1012  | 0.00   |
| Seagate   | ST500DM009-2DM14C  | 500 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD15EURS-63S48Y0   | 1.5 TB | 1       | 11    | 26    | 0.00   |
| WDC       | WD2500BB-22RDA0    | 250 GB | 1       | 655   | 1524  | 0.00   |
| Hitachi   | HTS725025A9A364    | 250 GB | 13      | 466   | 1119  | 0.00   |
| Toshiba   | MK8025GAS          | 80 GB  | 1       | 22    | 58    | 0.00   |
| Seagate   | ST3500321CS        | 500 GB | 1       | 48    | 137   | 0.00   |
| WDC       | WD3200L22X-00JVPT0 | 320 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD2500BEKT-60F3T1  | 250 GB | 1       | 529   | 1610  | 0.00   |
| Hitachi   | HTS542580K9A300    | 80 GB  | 1       | 332   | 1012  | 0.00   |
| Seagate   | ST250LT012-9WS141  | 250 GB | 4       | 337   | 1077  | 0.00   |
| Seagate   | ST980817AS         | 80 GB  | 1       | 310   | 1009  | 0.00   |
| WDC       | WD5000LPLX-60ZNTT0 | 500 GB | 1       | 0     | 0     | 0.00   |
| Samsung   | SV2011H            | 20 GB  | 1       | 0     | 3     | 0.00   |
| WDC       | WD2500AAJS-55B4A0  | 250 GB | 1       | 476   | 2020  | 0.00   |
| Toshiba   | MQ01ABB200         | 2 TB   | 1       | 152   | 704   | 0.00   |
| WDC       | WD800 AAJS-00PSA0  | 80 GB  | 1       | 97    | 459   | 0.00   |
| HGST      | HUS726020ALA610    | 2 TB   | 1       | 0     | 0     | 0.00   |
| Seagate   | ST9500424AS        | 500 GB | 1       | 200   | 1009  | 0.00   |
| Maxtor    | 7L300S0            | 304 GB | 1       | 5     | 33    | 0.00   |
| Seagate   | ST3160316CS        | 160 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD2005FBYZ-01YCBB1 | 2 TB   | 1       | 0     | 0     | 0.00   |
| WDC       | WD3200BEKX-60B7WT0 | 320 GB | 1       | 0     | 0     | 0.00   |
| Seagate   | ST980829A          | 80 GB  | 1       | 222   | 2022  | 0.00   |
| Maxtor    | 7L300R0            | 304 GB | 1       | 11    | 116   | 0.00   |
| Toshiba   | MK8025GAL          | 80 GB  | 1       | 78    | 1017  | 0.00   |
| Maxtor    | 53073H6            | 30 GB  | 1       | 121   | 2068  | 0.00   |
| Seagate   | ST9320312AS        | 320 GB | 1       | 69    | 1193  | 0.00   |
| Hitachi   | HTS548060M9AT00    | 64 GB  | 1       | 35    | 655   | 0.00   |
| Maxtor    | 6L200S0            | 208 GB | 1       | 2     | 39    | 0.00   |
| CLOVER    | CN-M500MBB         | 500 GB | 1       | 0     | 0     | 0.00   |
| Seagate   | ST3000VX010-2H916L | 3 TB   | 2       | 0     | 0     | 0.00   |
| WDC       | WD60PURX-64T0ZY0   | 6 TB   | 1       | 0     | 0     | 0.00   |
| WDC       | WD60PURX-64T0ZY1   | 6 TB   | 1       | 0     | 0     | 0.00   |
| Maxtor    | STM380215A         | 80 GB  | 1       | 44    | 1701  | 0.00   |
| Toshiba   | MK1676GSX          | 160 GB | 1       | 22    | 893   | 0.00   |
| Seagate   | ST380020A          | 80 GB  | 1       | 2     | 225   | 0.00   |
| Samsung   | HS06THB            | 64 GB  | 1       | 2     | 2087  | 0.00   |
| Hitachi   | HTS721060G9AT00    | 64 GB  | 1       | 0     | 37    | 0.00   |

HDD by Family
--------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

| MFG       | Family                 | Models | Samples | Days  | Err   | Rating |
|-----------|------------------------|--------|---------|-------|-------|--------|
| Samsung   | SpinPoint V20400       | 1      | 1       | 5713  | 0     | 15.65  |
| Seagate   | Barracuda ES+          | 1      | 1       | 2169  | 0     | 5.94   |
| Samsung   | SpinPoint F3 RE        | 1      | 1       | 1865  | 0     | 5.11   |
| WDC       | RE4-GP                 | 4      | 8       | 1784  | 1     | 4.49   |
| HP        | RE3                    | 1      | 1       | 1490  | 0     | 4.08   |
| HP        | Constellation ES.3     | 1      | 1       | 1370  | 0     | 3.76   |
| Hitachi   | CinemaStar 5K320       | 1      | 1       | 1281  | 0     | 3.51   |
| WDC       | Raptor X               | 1      | 1       | 1164  | 0     | 3.19   |
| Toshiba   | 1.8" HDD MK..17GSG     | 1      | 1       | 1162  | 0     | 3.18   |
| Samsung   | SpinPoint              | 2      | 3       | 1164  | 3     | 3.04   |
| Hitachi   | Deskstar E7K500        | 1      | 1       | 1103  | 0     | 3.02   |
| WDC       | RE2                    | 6      | 10      | 1297  | 60    | 2.84   |
| Hitachi   | Deskstar 7K2000        | 1      | 14      | 1448  | 6     | 2.81   |
| Toshiba   | 3.5" HDD               | 1      | 1       | 1008  | 0     | 2.76   |
| WDC       | RE2-GP                 | 1      | 1       | 989   | 0     | 2.71   |
| Seagate   | Constellation.2        | 2      | 2       | 983   | 0     | 2.69   |
| Hitachi   | Ultrastar A7K1000      | 3      | 5       | 1362  | 1     | 2.62   |
| HGST      | Ultrastar 7K4000       | 4      | 20      | 986   | 2     | 2.55   |
| Seagate   | U5                     | 2      | 2       | 875   | 0     | 2.40   |
| Toshiba   | 2.5" HDD MQ01ABF..H    | 1      | 2       | 873   | 0     | 2.39   |
| Hitachi   | Deskstar 7K3000        | 4      | 40      | 1040  | 36    | 2.36   |
| Quantum   | Fireball Plus AS       | 2      | 2       | 845   | 0     | 2.32   |
| Maxtor    | MaXLine III (SATA/300) | 2      | 3       | 963   | 1     | 2.30   |
| Seagate   | Enterprise NAS HDD     | 1      | 1       | 836   | 0     | 2.29   |
| Hitachi   | Ultrastar 7K3000       | 3      | 20      | 838   | 1     | 2.19   |
| Hitachi   | Deskstar 7K1000        | 2      | 12      | 1110  | 13    | 2.18   |
| WDC       | Red Pro                | 1      | 1       | 782   | 0     | 2.14   |
| HP        | Proliant HardDrive     | 5      | 5       | 1523  | 46    | 2.10   |
| Hitachi   | Deskstar 5K3000        | 3      | 17      | 943   | 21    | 2.06   |
| Seagate   | NAS HDD                | 7      | 22      | 802   | 92    | 2.02   |
| HGST      | Deskstar NAS           | 4      | 13      | 726   | 0     | 1.99   |
| Seagate   | Archive HDD            | 1      | 1       | 718   | 0     | 1.97   |
| WDC       | Caviar SE16            | 5      | 26      | 961   | 20    | 1.95   |
| Seagate   | Barracuda 7200.8       | 8      | 33      | 1086  | 118   | 1.88   |
| WDC       | Raptor                 | 12     | 16      | 1171  | 10    | 1.84   |
| Toshiba   | 3.5" HDD DT01ABA..V    | 2      | 2       | 642   | 0     | 1.76   |
| Hitachi   | Deskstar 5K1000        | 3      | 22      | 765   | 63    | 1.76   |
| Seagate   | Desktop HDD.15         | 4      | 24      | 648   | 1     | 1.75   |
| WDC       | Caviar Black           | 37     | 289     | 842   | 43    | 1.74   |
| WDC       | RE                     | 15     | 34      | 784   | 58    | 1.73   |
| Hitachi   | Deskstar 7K80          | 6      | 62      | 899   | 39    | 1.72   |
| Seagate   | Barracuda ES           | 6      | 32      | 1057  | 400   | 1.72   |
| WDC       | Caviar SE              | 136    | 404     | 878   | 24    | 1.68   |
| HGST      | Travelstar 5K1500      | 2      | 3       | 928   | 10    | 1.62   |
| Apple     | Seagate SpinPoint      | 1      | 1       | 589   | 0     | 1.61   |
| Toshiba   | 2.5" HDD MK..32GSX     | 1      | 4       | 579   | 0     | 1.59   |
| Toshiba   | 2.5" HDD MQ01ABC       | 1      | 1       | 574   | 0     | 1.57   |
| Seagate   | SV35.5                 | 1      | 2       | 938   | 2     | 1.56   |
| Hitachi   | Deskstar T7K500        | 8      | 44      | 1033  | 88    | 1.55   |
| Apple     | TOSHIBA MK..65GSXF     | 1      | 1       | 560   | 0     | 1.54   |
| Fujitsu   | MPA..MPG               | 5      | 6       | 711   | 42    | 1.53   |
| Seagate   | Constellation ES.2 ... | 1      | 4       | 553   | 0     | 1.52   |
| WDC       | RE3                    | 13     | 39      | 831   | 5     | 1.50   |
| Samsung   | SpinPoint F4 EG (AF)   | 2      | 18      | 846   | 54    | 1.50   |
| Hitachi   | Deskstar T7K250        | 5      | 25      | 1056  | 25    | 1.49   |
| WDC       | VelociRaptor           | 21     | 39      | 625   | 2     | 1.49   |
| Seagate   | Barracuda Green (AF)   | 4      | 112     | 830   | 195   | 1.48   |
| HGST      | Ultrastar DC HC520 ... | 1      | 1       | 534   | 0     | 1.46   |
| Samsung   | SpinPoint F3           | 4      | 160     | 714   | 49    | 1.46   |
| Seagate   | Barracuda XT           | 2      | 13      | 636   | 124   | 1.41   |
| Seagate   | Video 3.5 HDD          | 8      | 17      | 547   | 1     | 1.40   |
| Toshiba   | 2.5" HDD MK..59GSXP... | 1      | 3       | 506   | 0     | 1.39   |
| Seagate   | SpinPoint M7E          | 2      | 11      | 518   | 2     | 1.37   |
| Seagate   | U9                     | 2      | 5       | 490   | 0     | 1.34   |
| Seagate   | Barracuda 7200.10      | 29     | 955     | 830   | 280   | 1.33   |
| Apple     | HGST Travelstar Z5K500 | 1      | 10      | 512   | 2     | 1.33   |
| Samsung   | SpinPoint T133         | 5      | 18      | 841   | 197   | 1.32   |
| Seagate   | Barracuda 5400.1       | 1      | 5       | 835   | 33    | 1.32   |
| Apple     | Seagate Barracuda      | 1      | 2       | 476   | 0     | 1.31   |
| Samsung   | SpinPoint F1 DT        | 11     | 171     | 860   | 186   | 1.30   |
| WDC       | Scorpio Blue EIDE      | 6      | 8       | 471   | 0     | 1.29   |
| Seagate   | Constellation ES.2     | 1      | 1       | 467   | 0     | 1.28   |
| Samsung   | SpinPoint VL40         | 1      | 1       | 2328  | 4     | 1.28   |
| Seagate   | Barracuda 7200.7 an... | 18     | 473     | 818   | 98    | 1.26   |
| Seagate   | DB35.3                 | 6      | 11      | 584   | 211   | 1.26   |
| Hitachi   | Deskstar 7K1000.C      | 13     | 357     | 677   | 52    | 1.25   |
| WDC       | Caviar Green           | 120    | 979     | 728   | 67    | 1.23   |
| Hitachi   | Ultrastar A7K2000      | 4      | 16      | 556   | 62    | 1.23   |
| Samsung   | SpinPoint F2 EG        | 3      | 67      | 772   | 187   | 1.18   |
| WDC       | Caviar                 | 58     | 125     | 719   | 44    | 1.18   |
| Hitachi   | CinemaStar 5K1000      | 3      | 3       | 604   | 2     | 1.16   |
| Seagate   | Constellation ES (S... | 3      | 12      | 1028  | 201   | 1.15   |
| Fujitsu   | MHW BH                 | 9      | 39      | 572   | 44    | 1.15   |
| HGST      | Ultrastar 7K6000       | 7      | 8       | 416   | 0     | 1.14   |
| Maxtor    | DiamondMax 10 (SATA... | 6      | 25      | 610   | 38    | 1.14   |
| Hitachi   | Deskstar 7K1000.B      | 11     | 76      | 887   | 57    | 1.12   |
| Seagate   | Momentus               | 4      | 8       | 710   | 190   | 1.11   |
| Hitachi   | Deskstar 7K160         | 7      | 127     | 839   | 103   | 1.11   |
| Hitachi   | Deskstar P7K500        | 9      | 126     | 877   | 69    | 1.10   |
| Seagate   | Constellation ES.3     | 4      | 30      | 432   | 35    | 1.09   |
| Seagate   | SpinPoint M9T          | 2      | 18      | 425   | 3     | 1.08   |
| WDC       | Elements / My Passport | 19     | 32      | 457   | 51    | 1.07   |
| WDC       | Red                    | 15     | 162     | 496   | 26    | 1.07   |
| Seagate   | Barracuda 7200.12      | 14     | 968     | 696   | 171   | 1.06   |
| Seagate   | Barracuda 7200.9       | 29     | 399     | 746   | 437   | 1.06   |
| WDC       | Caviar Blue            | 273    | 2169    | 589   | 47    | 1.05   |
| Seagate   | Barracuda 7200.7       | 1      | 2       | 1049  | 105   | 1.04   |
| ExcelStor | Jupiter                | 6      | 13      | 666   | 15    | 1.03   |
| Seagate   | Constellation CS       | 2      | 8       | 373   | 0     | 1.02   |
| Seagate   | SpinPoint D8X          | 1      | 2       | 559   | 404   | 1.02   |
| WDC       | RE4                    | 13     | 58      | 564   | 2     | 1.02   |
| Seagate   | Barracuda              | 2      | 7       | 369   | 0     | 1.01   |
| Seagate   | Barracuda SpinPoint F3 | 2      | 41      | 462   | 9     | 1.01   |
| WDC       | Caviar Blue EIDE       | 16     | 86      | 648   | 73    | 1.00   |
| Samsung   | SpinPoint F3 EG        | 3      | 22      | 591   | 187   | 0.99   |
| WDC       | Se                     | 2      | 3       | 355   | 0     | 0.97   |
| WDC       | Green Mobile           | 1      | 1       | 354   | 0     | 0.97   |
| Toshiba   | 2.5" HDD MK..61GSY     | 1      | 1       | 354   | 0     | 0.97   |
| Hitachi   | CinemaStar P7K500      | 1      | 2       | 1010  | 2     | 0.97   |
| WDC       | Green                  | 1      | 1       | 1049  | 2     | 0.96   |
| Seagate   | Pipeline HD Mini       | 3      | 7       | 877   | 249   | 0.93   |
| Samsung   | SpinPoint P80 SD       | 7      | 179     | 831   | 370   | 0.92   |
| WDC       | AV-GP                  | 26     | 54      | 443   | 53    | 0.91   |
| Seagate   | Barracuda LP           | 4      | 55      | 883   | 435   | 0.89   |
| WDC       | Black                  | 12     | 70      | 355   | 1     | 0.88   |
| Seagate   | Barracuda ES.2         | 4      | 28      | 946   | 465   | 0.86   |
| Seagate   | Momentus XT (AF)       | 1      | 10      | 371   | 106   | 0.85   |
| MediaMax  | WL5000                 | 1      | 1       | 308   | 0     | 0.85   |
| Fujitsu   | MHY BH                 | 5      | 45      | 510   | 187   | 0.84   |
| Maxtor    | DiamondMax 21          | 16     | 161     | 670   | 379   | 0.84   |
| Samsung   | SpinPoint MT2          | 1      | 2       | 303   | 0     | 0.83   |
| Samsung   | SpinPoint T166         | 7      | 121     | 786   | 389   | 0.83   |
| Samsung   | SpinPoint F1 EG        | 1      | 2       | 483   | 9     | 0.83   |
| WDC       | Scorpio                | 1      | 1       | 300   | 0     | 0.82   |
| Seagate   | Barracuda ATA V        | 3      | 4       | 1503  | 35    | 0.82   |
| WDC       | AV                     | 14     | 25      | 568   | 70    | 0.80   |
| Samsung   | SpinPoint M7E (AF)     | 4      | 94      | 466   | 79    | 0.80   |
| MediaMax  | WL1000                 | 2      | 2       | 509   | 6     | 0.80   |
| Fujitsu   | MHW BJ                 | 2      | 2       | 289   | 0     | 0.79   |
| Seagate   | SV35                   | 12     | 74      | 385   | 169   | 0.79   |
| Seagate   | Barracuda 7200.14 (AF) | 23     | 1307    | 411   | 108   | 0.79   |
| Seagate   | Constellation ES (S... | 3      | 18      | 792   | 52    | 0.79   |
| HP        | Ultrastar 7K4000       | 1      | 1       | 1419  | 4     | 0.78   |
| Toshiba   | 2.5" HDD MK..58GSX     | 1      | 3       | 452   | 3     | 0.78   |
| Seagate   | UX                     | 1      | 5       | 629   | 16    | 0.78   |
| Seagate   | Barracuda ATA IV       | 4      | 42      | 617   | 25    | 0.77   |
| Fujitsu   | MHX BT                 | 2      | 5       | 619   | 30    | 0.77   |
| WDC       | Scorpio Blue           | 188    | 1521    | 414   | 57    | 0.76   |
| Fujitsu   | MHZ BH                 | 9      | 56      | 507   | 314   | 0.76   |
| Hitachi   | Travelstar 5K500.B     | 12     | 307     | 496   | 157   | 0.75   |
| WDC       | Scorpio Black          | 40     | 122     | 398   | 110   | 0.75   |
| WDC       | Black UltraSlim        | 1      | 1       | 267   | 0     | 0.73   |
| Apple     | Hitachi-HGST Travel... | 1      | 11      | 294   | 184   | 0.72   |
| HGST      | CinemaStar Z5K500      | 1      | 1       | 523   | 1     | 0.72   |
| Seagate   | Surveillance           | 5      | 10      | 260   | 0     | 0.71   |
| Seagate   | Barracuda V            | 1      | 1       | 259   | 0     | 0.71   |
| Seagate   | Pipeline HD 5900.2     | 6      | 37      | 472   | 245   | 0.71   |
| IBM/Hi... | Deskstar GXP-180       | 4      | 5       | 603   | 7     | 0.70   |
| Maxtor    | DiamondMax Plus D740X  | 2      | 3       | 834   | 4     | 0.70   |
| Toshiba   | 3.5" DT01ABA Deskto... | 1      | 2       | 254   | 0     | 0.70   |
| Seagate   | Momentus 7200.3        | 5      | 9       | 638   | 28    | 0.70   |
| Fujitsu   | MHV                    | 22     | 58      | 429   | 16    | 0.69   |
| Toshiba   | 3.5" HDD DT01ACA       | 4      | 514     | 281   | 29    | 0.68   |
| Hitachi   | Travelstar 7K200       | 6      | 11      | 608   | 117   | 0.67   |
| Samsung   | SpinPoint PL40         | 1      | 1       | 4382  | 17    | 0.67   |
| Hitachi   | Travelstar 5K750       | 3      | 222     | 418   | 366   | 0.66   |
| Toshiba   | 2.5" HDD MQ01UBB       | 1      | 1       | 242   | 0     | 0.66   |
| Fujitsu   | MHW AT                 | 1      | 1       | 241   | 0     | 0.66   |
| Toshiba   | 2.5" HDD               | 15     | 44      | 456   | 41    | 0.66   |
| Samsung   | SpinPoint F4           | 1      | 18      | 423   | 68    | 0.66   |
| Toshiba   | 3.5" MG03ACAxxx(Y) ... | 3      | 11      | 281   | 2     | 0.65   |
| Hitachi   | Travelstar Z7K500      | 1      | 8       | 375   | 670   | 0.65   |
| Seagate   | Video 2.5              | 2      | 3       | 236   | 0     | 0.65   |
| Seagate   | LD25.2                 | 2      | 2       | 383   | 1     | 0.65   |
| Seagate   | Momentus 5400.2        | 13     | 38      | 426   | 400   | 0.64   |
| Hitachi   | Travelstar 7K320       | 9      | 17      | 583   | 680   | 0.64   |
| Seagate   | Maxtor DiamondMax 23   | 4      | 49      | 613   | 265   | 0.64   |
| Seagate   | Desktop SSHD           | 5      | 46      | 311   | 109   | 0.64   |
| WDC       | Blue SSHD              | 2      | 2       | 230   | 0     | 0.63   |
| Hitachi   | Deskstar 7K250         | 6      | 11      | 759   | 336   | 0.63   |
| Samsung   | SpinPoint M7           | 3      | 93      | 360   | 55    | 0.63   |
| Seagate   | Momentus 7200.2        | 5      | 12      | 688   | 364   | 0.63   |
| Seagate   | Momentus 7200.4        | 7      | 129     | 504   | 338   | 0.62   |
| Seagate   | Momentus 7200.5        | 4      | 60      | 359   | 78    | 0.62   |
| Hitachi   | Travelstar 5K1000      | 3      | 15      | 395   | 685   | 0.62   |
| Hitachi   | CinemaStar 7K1000.B    | 2      | 4       | 218   | 0     | 0.60   |
| Toshiba   | X300                   | 2      | 8       | 218   | 0     | 0.60   |
| Samsung   | SpinPoint M8 (AF)      | 5      | 44      | 398   | 80    | 0.59   |
| Toshiba   | 2.5" HDD MQ01UBD       | 2      | 4       | 214   | 0     | 0.59   |
| Toshiba   | 2.5" HDD MK..55GSX     | 1      | 2       | 392   | 4     | 0.59   |
| Seagate   | SpinPoint M8 (AF)      | 6      | 604     | 296   | 49    | 0.59   |
| IBM/Hi... | Deskstar 120GXP        | 4      | 7       | 697   | 87    | 0.58   |
| Samsung   | SpinPoint P80          | 18     | 92      | 590   | 149   | 0.56   |
| Samsung   | SpinPoint S250         | 2      | 44      | 806   | 678   | 0.55   |
| Maxtor    | DiamondMax D540X-4K    | 3      | 3       | 582   | 16    | 0.54   |
| HGST      | Travelstar 7K1000      | 3      | 140     | 238   | 76    | 0.54   |
| HGST      | Travelstar 5K1000      | 5      | 147     | 292   | 280   | 0.54   |
| Hitachi   | Travelstar 7K100       | 4      | 7       | 327   | 11    | 0.54   |
| Seagate   | Momentus 5400 PSD      | 2      | 3       | 352   | 338   | 0.53   |
| Seagate   | Barracuda ATA III      | 1      | 1       | 194   | 0     | 0.53   |
| Hitachi   | Travelstar Z5K500      | 3      | 105     | 322   | 123   | 0.53   |
| Toshiba   | 2.5" HDD MQ01ABD       | 5      | 378     | 270   | 104   | 0.53   |
| Hitachi   | Deskstar 7K1000.D      | 2      | 60      | 561   | 477   | 0.52   |
| WDC       | Protege                | 6      | 9       | 652   | 14    | 0.52   |
| Samsung   | SpinPoint MP5          | 3      | 7       | 371   | 187   | 0.52   |
| Samsung   | SpinPoint S166         | 3      | 48      | 796   | 502   | 0.52   |
| Hitachi   | Travelstar Z7K320      | 1      | 22      | 337   | 466   | 0.52   |
| WDC       | Gold                   | 4      | 6       | 189   | 0     | 0.52   |
| Toshiba   | 2.5" HDD MQ02ABD..H    | 1      | 5       | 185   | 0     | 0.51   |
| Magnet... | Unknown                | 2      | 2       | 185   | 0     | 0.51   |
| Toshiba   | 2.5" HDD MQ03UBB       | 2      | 4       | 187   | 2     | 0.51   |
| Maxtor    | DiamondMax 20          | 5      | 19      | 564   | 324   | 0.50   |
| Samsung   | SpinPoint F1 RE        | 1      | 2       | 374   | 51    | 0.49   |
| Maxtor    | DiamondMax 17          | 2      | 9       | 314   | 101   | 0.48   |
| Toshiba   | 3.5" HDD E300          | 2      | 4       | 175   | 0     | 0.48   |
| Hitachi   | CinemaStar 5K1000.B    | 1      | 1       | 169   | 0     | 0.47   |
| HP        | 250GB SATA disk VB0... | 1      | 4       | 949   | 10    | 0.46   |
| Hitachi   | Deskstar 7K500         | 1      | 2       | 1300  | 24    | 0.46   |
| WDC       | Blue Mobile            | 79     | 827     | 195   | 13    | 0.46   |
| WDC       | Black SSHD             | 1      | 5       | 168   | 0     | 0.46   |
| Toshiba   | L200                   | 2      | 3       | 166   | 0     | 0.46   |
| WDC       | Blue UltraSlim         | 1      | 1       | 166   | 0     | 0.46   |
| WDC       | Purple                 | 10     | 24      | 217   | 7     | 0.45   |
| Seagate   | Momentus 5400.3        | 7      | 100     | 454   | 495   | 0.45   |
| Hitachi   | Travelstar Z5K320      | 3      | 160     | 301   | 298   | 0.44   |
| Seagate   | Barracuda Compute      | 1      | 2       | 161   | 0     | 0.44   |
| HGST      | Travelstar Z7K500      | 3      | 107     | 219   | 139   | 0.43   |
| Hitachi   | Travelstar 5K320       | 10     | 93      | 547   | 242   | 0.43   |
| Fujitsu   | MHT                    | 4      | 4       | 340   | 6     | 0.43   |
| Hitachi   | Travelstar 5K250       | 9      | 138     | 534   | 129   | 0.43   |
| Seagate   | Momentus 5400.4        | 3      | 55      | 460   | 334   | 0.43   |
| WDC       | Black Mobile           | 25     | 112     | 167   | 4     | 0.43   |
| Fujitsu   | MHZ BT                 | 1      | 1       | 155   | 0     | 0.43   |
| Seagate   | MobileMax-2            | 1      | 1       | 155   | 0     | 0.43   |
| Toshiba   | 3.5" MD04ACA Enterp... | 2      | 3       | 155   | 0     | 0.42   |
| Samsung   | SpinPoint V80          | 3      | 4       | 597   | 63    | 0.42   |
| Fujitsu   | MJA BH                 | 7      | 28      | 368   | 198   | 0.42   |
| Hitachi   | Travelstar 5K500       | 1      | 5       | 469   | 5     | 0.41   |
| Toshiba   | Enterprise Surveill... | 1      | 1       | 1037  | 6     | 0.41   |
| Hitachi   | Travelstar 7K750       | 2      | 20      | 379   | 221   | 0.40   |
| WDC       | Blue                   | 25     | 125     | 146   | 1     | 0.39   |
| Toshiba   | 2.5" HDD MK..63GSX     | 2      | 12      | 583   | 23    | 0.39   |
| Hitachi   | Travelstar 5K120       | 1      | 3       | 438   | 5     | 0.39   |
| Toshiba   | 2.5" HDD MK..75GSX     | 4      | 55      | 361   | 397   | 0.38   |
| Seagate   | U6                     | 3      | 12      | 567   | 48    | 0.38   |
| Toshiba   | 2.5" HDD MK..59GSXP    | 7      | 93      | 362   | 303   | 0.38   |
| Toshiba   | 2.5" HDD MK..37GSX     | 1      | 15      | 456   | 158   | 0.37   |
| Hitachi   | Deskstar E7K1000       | 2      | 3       | 1464  | 64    | 0.37   |
| Samsung   | SpinPoint M            | 2      | 6       | 263   | 5     | 0.37   |
| Quantum   | Fireball lct15         | 3      | 3       | 226   | 2     | 0.36   |
| Toshiba   | 2.5" HDD MK..55GSX     | 5      | 48      | 385   | 82    | 0.36   |
| Samsung   | SpinPoint P120         | 5      | 68      | 807   | 612   | 0.35   |
| Seagate   | Momentus XT            | 1      | 7       | 374   | 299   | 0.35   |
| Hitachi   | Travelstar 5K100       | 9      | 40      | 405   | 26    | 0.35   |
| Hitachi   | Travelstar 5K160       | 9      | 127     | 479   | 53    | 0.34   |
| Toshiba   | 1.8" HDD MK..16GSG     | 1      | 3       | 272   | 4     | 0.34   |
| Seagate   | Laptop HDD             | 1      | 1       | 124   | 0     | 0.34   |
| Toshiba   | 1.8" HDD               | 4      | 7       | 292   | 17    | 0.34   |
| Seagate   | SV35.2                 | 2      | 6       | 662   | 1173  | 0.34   |
| Seagate   | Momentus 5400.6        | 10     | 658     | 440   | 493   | 0.34   |
| Seagate   | SpinPoint F4           | 1      | 4       | 187   | 108   | 0.33   |
| Seagate   | Laptop SSHD            | 7      | 108     | 218   | 101   | 0.33   |
| Seagate   | Momentus Thin          | 5      | 130     | 347   | 580   | 0.33   |
| Seagate   | Momentus 5400.7 (AF)   | 2      | 9       | 289   | 358   | 0.33   |
| Seagate   | Momentus 5400.7        | 1      | 6       | 465   | 468   | 0.33   |
| IBM       | Deskstar 40GV & 75G... | 2      | 3       | 1137  | 26    | 0.32   |
| Toshiba   | 2.5" HDD MQ01ABF       | 2      | 21      | 154   | 49    | 0.32   |
| HGST      | Travelstar Z5K500      | 5      | 329     | 227   | 268   | 0.32   |
| Toshiba   | 2.5" HDD MK..34GSX     | 2      | 12      | 356   | 180   | 0.32   |
| WDC       | Unknown                | 1      | 1       | 1047  | 8     | 0.32   |
| Toshiba   | P300                   | 4      | 133     | 120   | 19    | 0.32   |
| Toshiba   | 2.5" HDD MQ01ABF       | 1      | 210     | 138   | 86    | 0.32   |
| Toshiba   | 2.5" HDD L200          | 2      | 7       | 115   | 0     | 0.32   |
| Toshiba   | N300                   | 2      | 3       | 113   | 0     | 0.31   |
| Hitachi   | Travelstar 7K500       | 8      | 53      | 396   | 729   | 0.31   |
| Toshiba   | 2.5" HDD MK..76GSX     | 6      | 13      | 150   | 139   | 0.31   |
| Toshiba   | 2.5" HDD MQ01ACF       | 2      | 7       | 135   | 149   | 0.31   |
| Toshiba   | 2.5" HDD MK..37GSX     | 2      | 36      | 471   | 50    | 0.31   |
| Seagate   | LD25 Series            | 2      | 2       | 111   | 0     | 0.30   |
| HGST      | Ultrastar 7K2          | 2      | 4       | 110   | 0     | 0.30   |
| Seagate   | Momentus 7200.1        | 2      | 7       | 552   | 471   | 0.30   |
| Toshiba   | 2.5" HDD MK..65GSX     | 13     | 147     | 453   | 312   | 0.30   |
| Seagate   | Momentus 4200.2        | 4      | 4       | 458   | 516   | 0.30   |
| Seagate   | Ultra Mobile HDD       | 2      | 3       | 107   | 0     | 0.30   |
| Seagate   | FireCuda 3.5           | 2      | 15      | 107   | 0     | 0.29   |
| China     | Unknown                | 1      | 1       | 106   | 0     | 0.29   |
| Toshiba   | 2.5" HDD MK..59GSM     | 1      | 12      | 472   | 308   | 0.29   |
| Seagate   | IronWolf               | 3      | 3       | 103   | 0     | 0.28   |
| Toshiba   | 2.5" HDD MK..46GSX     | 4      | 33      | 466   | 48    | 0.27   |
| HGST      | Travelstar Z5K1000     | 2      | 18      | 116   | 57    | 0.27   |
| Seagate   | Barracuda 3.5          | 8      | 130     | 108   | 7     | 0.27   |
| MediaMax  | WL320                  | 1      | 1       | 94    | 0     | 0.26   |
| Seagate   | Laptop Thin SSHD       | 1      | 1       | 94    | 0     | 0.26   |
| Toshiba   | 3.5" MG04ACA Enterp... | 2      | 5       | 93    | 2     | 0.24   |
| IBM/Hi... | Deskstar 60GXP         | 2      | 3       | 1032  | 106   | 0.24   |
| Toshiba   | 2.5" HDD MQ04UBF       | 1      | 2       | 83    | 0     | 0.23   |
| Toshiba   | 1.8" HDD MK..33GSG     | 2      | 3       | 634   | 316   | 0.21   |
| Samsung   | SpinPoint M40/60/80    | 8      | 15      | 503   | 223   | 0.21   |
| Seagate   | Enterprise Capacity... | 4      | 6       | 73    | 0     | 0.20   |
| Seagate   | Barracuda 2.5 5400     | 6      | 56      | 80    | 2     | 0.20   |
| Toshiba   | 2.5" HDD MK..52GSX     | 5      | 43      | 446   | 140   | 0.20   |
| Seagate   | SpinPoint M8U (USB)    | 1      | 6       | 69    | 0     | 0.19   |
| Seagate   | Laptop Thin HDD        | 7      | 541     | 202   | 419   | 0.19   |
| Seagate   | SpinPoint M9TU (USB)   | 1      | 1       | 67    | 0     | 0.19   |
| Seagate   | Barracuda 7200.11      | 11     | 266     | 799   | 349   | 0.19   |
| Seagate   | Momentus 5400.5        | 4      | 60      | 415   | 192   | 0.18   |
| IBM/Hi... | Hitachi Travelstar ... | 4      | 11      | 314   | 43    | 0.15   |
| IBM/Hi... | Travelstar 60GH and... | 1      | 1       | 52    | 0     | 0.14   |
| Hitachi   | Travelstar 4K40        | 1      | 6       | 456   | 186   | 0.14   |
| Toshiba   | 2.5" HDD MK..56GSY     | 5      | 12      | 110   | 184   | 0.14   |
| Seagate   | SV35.3                 | 2      | 2       | 831   | 12    | 0.13   |
| HGST      | Travelstar Z5K1        | 1      | 10      | 46    | 0     | 0.13   |
| Seagate   | FireCuda 2.5           | 2      | 15      | 103   | 135   | 0.13   |
| Toshiba   | 2.5" HDD MK..59GSM     | 2      | 19      | 378   | 984   | 0.13   |
| HGST      | Travelstar Z5K500.B    | 1      | 13      | 45    | 0     | 0.12   |
| Toshiba   | 2.5" HDD MK..61GSY[N]  | 4      | 20      | 101   | 197   | 0.12   |
| Samsung   | SpinPoint N2           | 2      | 2       | 46    | 1044  | 0.12   |
| Seagate   | Mobile HDD             | 2      | 69      | 50    | 65    | 0.12   |
| WDC       | Scorpio EIDE           | 6      | 6       | 235   | 69    | 0.11   |
| WDC       | Shrek LT 2.5           | 1      | 1       | 41    | 0     | 0.11   |
| Toshiba   | 3.5" HDD N300          | 1      | 2       | 39    | 0     | 0.11   |
| Toshiba   | 1.8" HDD               | 3      | 7       | 235   | 210   | 0.11   |
| Toshiba   | 1.8" HDD MK..29GSG     | 2      | 4       | 361   | 568   | 0.10   |
| Hitachi   | Travelstar 4K120       | 3      | 5       | 521   | 18    | 0.10   |
| Toshiba   | 2.5" HDD MK..46GSX     | 1      | 9       | 408   | 51    | 0.10   |
| Samsung   | SpinPoint M5           | 5      | 67      | 367   | 390   | 0.10   |
| Toshiba   | 2.5" HDD MQ04ABF       | 1      | 13      | 34    | 0     | 0.10   |
| MicroData | Unknown                | 1      | 1       | 288   | 8     | 0.09   |
| Samsung   | SpinPoint V40+         | 2      | 3       | 1003  | 159   | 0.08   |
| Seagate   | U8                     | 1      | 1       | 754   | 24    | 0.08   |
| Samsung   | SpinPoint V60          | 1      | 4       | 957   | 88    | 0.08   |
| Maxtor    | DiamondMax 22          | 4      | 27      | 901   | 406   | 0.08   |
| Toshiba   | 2.5" HDD MQ01ABD       | 1      | 1       | 27    | 0     | 0.08   |
| MARSHAL   | Unknown                | 1      | 1       | 279   | 9     | 0.08   |
| WDC       | HGST Ultrastar He10    | 1      | 1       | 25    | 0     | 0.07   |
| Samsung   | SpinPoint M6           | 3      | 11      | 335   | 291   | 0.07   |
| Seagate   | Mobile USB Momentus    | 1      | 1       | 24    | 0     | 0.07   |
| Seagate   | DB35.4                 | 1      | 1       | 1067  | 42    | 0.07   |
| MediaMax  | WL250                  | 2      | 3       | 43    | 3     | 0.07   |
| Toshiba   | 2.5" HDD L200 Slim     | 1      | 2       | 24    | 0     | 0.07   |
| Toshiba   | 2.5" HDD               | 1      | 1       | 23    | 0     | 0.06   |
| Hitachi   | Travelstar DK23XX/D... | 3      | 3       | 477   | 170   | 0.06   |
| IBM       | Travelstar 25GS, 18... | 1      | 1       | 118   | 5     | 0.05   |
| Toshiba   | 2.5" HDD H200          | 2      | 3       | 18    | 0     | 0.05   |
| Seagate   | FreePlay               | 2      | 8       | 99    | 895   | 0.05   |
| Seagate   | BarraCuda Pro          | 3      | 15      | 43    | 1     | 0.05   |
| Seagate   | Constellation.2 (SATA) | 2      | 3       | 17    | 0     | 0.05   |
| Maxtor    | Fireball 3             | 5      | 8       | 50    | 4     | 0.05   |
| Toshiba   | 2.5" HDD MK..65GSX     | 2      | 3       | 368   | 31    | 0.04   |
| Seagate   | Video 3.5              | 1      | 1       | 15    | 0     | 0.04   |
| Maxtor    | DiamondMax 10 (ATA/... | 17     | 34      | 25    | 121   | 0.04   |
| Seagate   | Unknown                | 1      | 1       | 14    | 0     | 0.04   |
| Seagate   | U10                    | 1      | 1       | 380   | 27    | 0.04   |
| Apple     | HGST Travelstar 5K750  | 2      | 2       | 265   | 77    | 0.04   |
| Seagate   | Pipeline HD 5900.1     | 2      | 4       | 444   | 58    | 0.03   |
| Seagate   | DB35.2                 | 2      | 2       | 1265  | 514   | 0.03   |
| Samsung   | SpinPoint M7U (USB)    | 1      | 1       | 11    | 0     | 0.03   |
| Hitachi   | Travelstar 5K80        | 3      | 3       | 214   | 230   | 0.03   |
| Maxtor    | MaXLine III (ATA/13... | 4      | 4       | 16    | 38    | 0.03   |
| Toshiba   | 2.5" HDD MK..76GSX     | 5      | 56      | 27    | 214   | 0.02   |
| Maxtor    | DiamondMax Plus 8      | 4      | 15      | 24    | 25    | 0.02   |
| LENOVO    | RE                     | 1      | 2       | 7     | 0     | 0.02   |
| Hitachi   | Ultrastar 7K4000       | 1      | 1       | 7     | 0     | 0.02   |
| Toshiba   | 2.5" HDD MQ02ABF..H    | 1      | 1       | 5     | 0     | 0.01   |
| Hitachi   | Travelstar E7K100      | 1      | 1       | 4     | 0     | 0.01   |
| Toshiba   | 2.5" HDD MK..59GSX     | 1      | 2       | 117   | 637   | 0.01   |
| Fujitsu   | MHZ BJ                 | 1      | 1       | 4     | 0     | 0.01   |
| Seagate   | Barracuda Pro          | 1      | 2       | 3     | 0     | 0.01   |
| Seagate   | BarraCuda              | 1      | 4       | 3     | 0     | 0.01   |
| Maxtor    | DiamondMax Plus 9      | 11     | 65      | 30    | 195   | 0.01   |
| Maxtor    | Fireball 541DX         | 1      | 6       | 23    | 75    | 0.01   |
| Maxtor    | DiamondMax 16          | 2      | 3       | 37    | 28    | 0.01   |
| Seagate   | SkyHawk                | 3      | 4       | 1     | 0     | 0.01   |
| Toshiba   | 2.5" HDD MQ02ABF       | 1      | 1       | 1     | 0     | 0.01   |
| Hitachi   | Ultrastar 5K3000       | 1      | 1       | 1045  | 595   | 0.00   |
| Maxtor    | DiamondMax D540X-4D    | 2      | 4       | 18    | 185   | 0.00   |
| Maxtor    | MaXLine Plus II        | 1      | 1       | 43    | 37    | 0.00   |
| CLOVER    | Hightech Utania        | 2      | 2       | 0     | 0     | 0.00   |
| HGST      | Unknown                | 1      | 1       | 8     | 10    | 0.00   |
| MediaMax  | WL400                  | 1      | 1       | 0     | 0     | 0.00   |
| HGST      | Travelstar Z7K500.B    | 1      | 2       | 0     | 0     | 0.00   |
| Toshiba   | 2.5" HDD MQ01ABB       | 1      | 1       | 152   | 704   | 0.00   |
| Maxtor    | DiamondMax Plus 40 ... | 1      | 1       | 121   | 2068  | 0.00   |

HDD by Vendor
-------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

| MFG         | Models | Samples | Days  | Err   | Rating |
|-------------|--------|---------|-------|-------|--------|
| HP          | 9      | 12      | 1307  | 23    | 1.75   |
| Quantum     | 5      | 5       | 474   | 2     | 1.14   |
| ExcelStor   | 6      | 13      | 666   | 15    | 1.03   |
| Apple       | 7      | 27      | 407   | 82    | 1.00   |
| WDC         | 1220   | 7406    | 538   | 44    | 1.00   |
| Samsung     | 122    | 1390    | 687   | 243   | 0.88   |
| Hitachi     | 209    | 2424    | 600   | 170   | 0.88   |
| Fujitsu     | 68     | 246     | 482   | 141   | 0.79   |
| Seagate     | 428    | 8110    | 538   | 231   | 0.79   |
| Magnetic... | 2      | 2       | 185   | 0     | 0.51   |
| HGST        | 43     | 817     | 262   | 191   | 0.50   |
| Maxtor      | 88     | 391     | 441   | 258   | 0.49   |
| Toshiba     | 164    | 2079    | 280   | 117   | 0.45   |
| IBM/Hitachi | 15     | 27      | 537   | 53    | 0.37   |
| MediaMax    | 7      | 8       | 194   | 3     | 0.36   |
| China       | 1      | 1       | 106   | 0     | 0.29   |
| IBM         | 3      | 4       | 882   | 21    | 0.26   |
| MicroData   | 1      | 1       | 288   | 8     | 0.09   |
| MARSHAL     | 1      | 1       | 279   | 9     | 0.08   |
| LENOVO      | 1      | 2       | 7     | 0     | 0.02   |
| CLOVER      | 2      | 2       | 0     | 0     | 0.00   |

SSD by Model
------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

See complete list of tested SSD samples in the Appendix 2 (All_SSD.md).

| MFG       | Model              | Size   | Samples | Days  | Err   | Rating |
|-----------|--------------------|--------|---------|-------|-------|--------|
| Kingston  | SH100S3120G        | 120 GB | 2       | 1711  | 0     | 4.69   |
| OCZ       | VERTEX2            | 40 GB  | 2       | 1543  | 0     | 4.23   |
| Corsair   | Force 3 SSD        | 180 GB | 4       | 1926  | 1     | 4.19   |
| Mushkin   | MKNSSDCR240GB      | 240 GB | 1       | 1513  | 0     | 4.15   |
| Corsair   | Force 3 SSD        | 240 GB | 2       | 1270  | 0     | 3.48   |
| Kingston  | SKC300S37A480G     | 480 GB | 1       | 1231  | 0     | 3.37   |
| Toshiba   | THNS064GG2BNAA     | 64 GB  | 2       | 1215  | 0     | 3.33   |
| Mushkin   | MKNSSDCR120GB      | 120 GB | 1       | 1164  | 0     | 3.19   |
| Samsung   | SSD 850 EVO        | 2 TB   | 1       | 1163  | 0     | 3.19   |
| Samsung   | MZ7WD240HCFV-00003 | 240 GB | 1       | 1154  | 0     | 3.16   |
| OCZ       | VERTEX2 3.5        | 120 GB | 1       | 1040  | 0     | 2.85   |
| SanDisk   | SD7UB2Q512G1122    | 512 GB | 1       | 1017  | 0     | 2.79   |
| Intel     | SSDSC2BA100G3      | 100 GB | 4       | 1128  | 1     | 2.71   |
| Samsung   | SSD 830 Series     | 64 GB  | 4       | 962   | 0     | 2.64   |
| Crucial   | CT120M500SSD3      | 120 GB | 2       | 933   | 8     | 2.54   |
| OCZ       | AGILITY4           | 128 GB | 3       | 922   | 0     | 2.53   |
| Kingston  | SVP100S296G        | 96 GB  | 1       | 918   | 0     | 2.52   |
| Crucial   | M4-CT256M4SSD2     | 256 GB | 8       | 925   | 256   | 2.47   |
| Crucial   | M4-CT128M4SSD1     | 128 GB | 4       | 902   | 0     | 2.47   |
| Samsung   | SSD PM800 2.5"     | 256 GB | 1       | 871   | 0     | 2.39   |
| Kingston  | SE50S3480G         | 480 GB | 2       | 859   | 0     | 2.35   |
| Apple     | SSD SM0256F        | 256 GB | 1       | 858   | 0     | 2.35   |
| Corsair   | Force GS           | 180 GB | 2       | 854   | 0     | 2.34   |
| Samsung   | MZMPC032HBCD-000D1 | 32 GB  | 1       | 840   | 0     | 2.30   |
| ADATA     | SSD S510           | 120 GB | 4       | 824   | 0     | 2.26   |
| Samsung   | MZ7GE240HMGR-00003 | 240 GB | 1       | 822   | 0     | 2.25   |
| Crucial   | CT250MX200SSD3     | 250 GB | 1       | 816   | 0     | 2.24   |
| Crucial   | M4-CT128M4SSD2     | 128 GB | 20      | 828   | 51    | 2.22   |
| OCZ       | VERTEX PLUS R2     | 61 GB  | 2       | 802   | 0     | 2.20   |
| OCZ       | DENRSTE251M45-0... | 100 GB | 1       | 801   | 0     | 2.20   |
| OCZ       | VERTEX PLUS R2     | 247 GB | 1       | 797   | 0     | 2.18   |
| Intel     | SSDSA2SH032G1GN    | 32 GB  | 1       | 795   | 0     | 2.18   |
| Toshiba   | THNSNH060GMCT      | 64 GB  | 1       | 787   | 0     | 2.16   |
| Micron    | MTFDDAT128MAM-1J2  | 128 GB | 1       | 783   | 0     | 2.15   |
| Corsair   | Force GS           | 90 GB  | 1       | 776   | 0     | 2.13   |
| Samsung   | SSD 830 Series     | 512 GB | 2       | 769   | 0     | 2.11   |
| Kingston  | SVP200S37A480G     | 480 GB | 1       | 765   | 0     | 2.10   |
| Toshiba   | THNSNJ120PCSZ      | 120 GB | 2       | 758   | 0     | 2.08   |
| Lite-On   | LCS-256L9S-11 2... | 256 GB | 1       | 739   | 0     | 2.02   |
| SanDisk   | SD5SE2128G1002E    | 128 GB | 2       | 729   | 0     | 2.00   |
| Corsair   | Force 3 SSD        | 120 GB | 7       | 716   | 0     | 1.96   |
| OCZ       | NOCTI              | 64 GB  | 1       | 704   | 0     | 1.93   |
| Crucial   | M4-CT064M4SSD2     | 64 GB  | 9       | 702   | 0     | 1.93   |
| Kingston  | SVP100S2128G       | 128 GB | 1       | 698   | 0     | 1.91   |
| Kingston  | SVP200S390G        | 90 GB  | 1       | 686   | 0     | 1.88   |
| Corsair   | Force 3 SSD        | 64 GB  | 9       | 686   | 0     | 1.88   |
| Kingston  | SNVP325S2128GB     | 128 GB | 1       | 674   | 0     | 1.85   |
| Kingston  | RBU-SNS8152S3128GF | 128 GB | 1       | 665   | 0     | 1.82   |
| Corsair   | Force GT           | 120 GB | 8       | 798   | 1     | 1.82   |
| OCZ       | VERTEX2            | 64 GB  | 5       | 653   | 0     | 1.79   |
| Intel     | SSDSC2MH120A2      | 120 GB | 1       | 646   | 0     | 1.77   |
| Kingston  | SV200S364G         | 64 GB  | 2       | 645   | 0     | 1.77   |
| Samsung   | SSD 840 EVO 120... | 120 GB | 1       | 641   | 0     | 1.76   |
| OCZ       | VECTOR180          | 240 GB | 2       | 641   | 0     | 1.76   |
| Kingston  | SVP200S37A240G     | 240 GB | 1       | 623   | 0     | 1.71   |
| OCZ       | VERTEX2            | 120 GB | 4       | 623   | 0     | 1.71   |
| Intel     | SSDSA2M040G2GC     | 40 GB  | 2       | 1007  | 3     | 1.69   |
| Samsung   | MZMPA128HMFU-00000 | 128 GB | 1       | 616   | 0     | 1.69   |
| Toshiba   | THNSNH256GMCT      | 256 GB | 1       | 612   | 0     | 1.68   |
| Samsung   | SSD 850 EVO M.2    | 120 GB | 2       | 607   | 0     | 1.66   |
| Samsung   | SSD 850 PRO        | 1 TB   | 3       | 606   | 0     | 1.66   |
| Intel     | SSDSC2CT080A4      | 80 GB  | 3       | 600   | 0     | 1.64   |
| Corsair   | Force 3 SSD        | 480 GB | 1       | 598   | 0     | 1.64   |
| Corsair   | Force GT           | 180 GB | 2       | 594   | 0     | 1.63   |
| OCZ       | DENCSTE351M16-0... | 240 GB | 1       | 585   | 0     | 1.60   |
| OCZ       | VERTEX2            | 115 GB | 1       | 581   | 0     | 1.59   |
| Kingston  | SVP200S360G        | 64 GB  | 4       | 572   | 0     | 1.57   |
| OCZ       | AGILITY4           | 64 GB  | 1       | 567   | 0     | 1.56   |
| OCZ       | REVODRIVE3         | 64 GB  | 4       | 564   | 0     | 1.55   |
| Samsung   | MZMPC128HBFU-000L1 | 128 GB | 1       | 559   | 0     | 1.53   |
| Patriot   | Torch LE           | 240 GB | 1       | 558   | 0     | 1.53   |
| OCZ       | AGILITY3           | 120 GB | 25      | 652   | 111   | 1.53   |
| Samsung   | MZ7TE512HMHP-000L2 | 512 GB | 2       | 552   | 0     | 1.51   |
| Toshiba   | THNSNH128GCST      | 128 GB | 1       | 549   | 0     | 1.51   |
| SanDisk   | SD6SB1M256G1002    | 256 GB | 1       | 548   | 0     | 1.50   |
| Kingston  | SMS100S264G        | 64 GB  | 2       | 547   | 0     | 1.50   |
| SK hynix  | SC300 SATA         | 512 GB | 1       | 546   | 0     | 1.50   |
| Apple     | SSD SM1024F        | 1 TB   | 1       | 545   | 0     | 1.49   |
| Samsung   | MZ7PC128HAFU-000   | 128 GB | 1       | 545   | 0     | 1.49   |
| OCZ       | VERTEX2 3.5        | 115 GB | 1       | 541   | 0     | 1.48   |
| SK hynix  | SC311 SATA         | 256 GB | 2       | 541   | 0     | 1.48   |
| Toshiba   | THNSFC256GAMJ      | 256 GB | 1       | 539   | 0     | 1.48   |
| Samsung   | MZHPV512HDGL-00000 | 512 GB | 1       | 536   | 0     | 1.47   |
| Samsung   | SSD 840 PRO Series | 128 GB | 16      | 579   | 4     | 1.46   |
| Kingston  | SH100S3240G        | 240 GB | 2       | 1170  | 2     | 1.42   |
| OCZ       | D2RSTK251E19-0200  | 200 GB | 1       | 511   | 0     | 1.40   |
| Samsung   | MZ7PA128HMCD-010L1 | 128 GB | 1       | 504   | 0     | 1.38   |
| OCZ       | D2RSTK251E14-0400  | 400 GB | 1       | 502   | 0     | 1.38   |
| Corsair   | Force GT           | 90 GB  | 4       | 610   | 1     | 1.36   |
| Transcend | TS128GSSD320       | 128 GB | 1       | 493   | 0     | 1.35   |
| Samsung   | SSD 830 Series     | 256 GB | 7       | 559   | 145   | 1.33   |
| SPCC      | SSD110             | 64 GB  | 4       | 482   | 0     | 1.32   |
| OCZ       | VERTEX3            | 64 GB  | 24      | 554   | 2     | 1.32   |
| Intel     | SSDSC2BW240A3L     | 240 GB | 1       | 480   | 0     | 1.32   |
| Toshiba   | Q300 Pro           | 256 GB | 2       | 478   | 0     | 1.31   |
| ADATA     | SP600              | 256 GB | 2       | 477   | 0     | 1.31   |
| Crucial   | CT1050MX300SSD1    | 1 TB   | 2       | 476   | 0     | 1.31   |
| Intel     | SSDSA2CW080G3      | 80 GB  | 5       | 475   | 0     | 1.30   |
| SanDisk   | SDSSDH240GG25      | 240 GB | 1       | 473   | 0     | 1.30   |
| Toshiba   | THNSNF128GMCS      | 128 GB | 2       | 471   | 0     | 1.29   |
| Verbatim  | SATA-III SSD       | 128 GB | 1       | 470   | 0     | 1.29   |
| KingSpec  | SPK-SF12-M120      | 120 GB | 1       | 468   | 0     | 1.28   |
| Toshiba   | THNSNH060GCST      | 64 GB  | 1       | 467   | 0     | 1.28   |
| Plextor   | PX-64M2S           | 64 GB  | 2       | 467   | 0     | 1.28   |
| Intel     | SSDSA2CW120G3      | 120 GB | 6       | 466   | 0     | 1.28   |
| ADATA     | SSD S396           | 32 GB  | 1       | 462   | 0     | 1.27   |
| OCZ       | AGILITY3           | 64 GB  | 24      | 520   | 2     | 1.25   |
| Corsair   | Performance Pro    | 128 GB | 1       | 450   | 0     | 1.23   |
| Samsung   | SSD 840 PRO Series | 512 GB | 4       | 570   | 1     | 1.23   |
| Plextor   | PX-128M2S          | 128 GB | 1       | 447   | 0     | 1.23   |
| Foxline   | FLDMMS128G         | 128 GB | 1       | 443   | 0     | 1.22   |
| OCZ       | VERTEX2            | 80 GB  | 1       | 442   | 0     | 1.21   |
| Corsair   | Force GT           | 64 GB  | 5       | 690   | 7     | 1.21   |
| Kingston  | SVP200S37A120G     | 120 GB | 7       | 502   | 154   | 1.20   |
| OCZ       | REVODRIVE X2       | 25 GB  | 4       | 435   | 0     | 1.19   |
| SanDisk   | SD8SN8U256G1122    | 256 GB | 1       | 434   | 0     | 1.19   |
| OCZ       | VERTEX3            | 120 GB | 46      | 637   | 38    | 1.19   |
| Phison    | SSDS30256XQC800... | 240 GB | 1       | 433   | 0     | 1.19   |
| OCZ       | VERTEX4            | 128 GB | 56      | 476   | 1     | 1.19   |
| Kingston  | SV200S3128G        | 128 GB | 6       | 432   | 0     | 1.19   |
| Samsung   | SSD 850 PRO        | 512 GB | 12      | 498   | 87    | 1.18   |
| ADATA     | SSD S511           | 120 GB | 1       | 430   | 0     | 1.18   |
| Samsung   | MZ7TE256HMHP-00000 | 256 GB | 1       | 427   | 0     | 1.17   |
| Samsung   | SSD 850 EVO        | 1 TB   | 18      | 554   | 1     | 1.17   |
| Kingston  | SKC380S360G        | 64 GB  | 1       | 420   | 0     | 1.15   |
| Kingston  | SMS200S3240G       | 240 GB | 1       | 419   | 0     | 1.15   |
| OCZ       | SOLID3             | 120 GB | 1       | 418   | 0     | 1.15   |
| Samsung   | SSD PM830 2.5" 7mm | 256 GB | 2       | 417   | 0     | 1.14   |
| Samsung   | SSD 840 EVO        | 250 GB | 31      | 416   | 33    | 1.13   |
| SanDisk   | SD6SB2M128G1022I   | 128 GB | 1       | 412   | 0     | 1.13   |
| Toshiba   | Q300 Pro           | 512 GB | 1       | 411   | 0     | 1.13   |
| Samsung   | MMCRE28G5MXP-0VBH1 | 128 GB | 1       | 410   | 0     | 1.12   |
| OCZ       | AGILITY3           | 240 GB | 6       | 618   | 1     | 1.12   |
| Plextor   | PX-512M7VC         | 512 GB | 2       | 404   | 0     | 1.11   |
| SanDisk   | SDSSDH2256G        | 256 GB | 1       | 403   | 0     | 1.10   |
| OCZ       | VERTEX3            | 128 GB | 2       | 402   | 0     | 1.10   |
| Toshiba   | THNSNH060GBST      | 64 GB  | 2       | 400   | 0     | 1.10   |
| Samsung   | SSD 840 EVO        | 752 GB | 2       | 399   | 0     | 1.09   |
| SanDisk   | SDSSDXP240G        | 240 GB | 2       | 398   | 0     | 1.09   |
| Samsung   | MZNLN128HCGR-00000 | 128 GB | 1       | 396   | 0     | 1.09   |
| Micron    | 1100 SATA          | 256 GB | 1       | 784   | 1     | 1.08   |
| OCZ       | VERTEX3            | 240 GB | 7       | 448   | 6     | 1.07   |
| Toshiba   | THNSFJ256GDNU A    | 256 GB | 1       | 390   | 0     | 1.07   |
| Samsung   | SSD PM830 mSATA    | 32 GB  | 7       | 389   | 0     | 1.07   |
| Smartbuy  | SSD                | 64 GB  | 6       | 386   | 0     | 1.06   |
| Kingston  | SNV425S264GB       | 64 GB  | 1       | 386   | 0     | 1.06   |
| Samsung   | MZ7TD256HAFV-000L9 | 256 GB | 1       | 385   | 0     | 1.06   |
| Samsung   | SSD 840 PRO Series | 256 GB | 20      | 385   | 0     | 1.06   |
| Crucial   | CT256MX100SSD1     | 256 GB | 12      | 383   | 0     | 1.05   |
| Samsung   | MMCRE28GFMXP-MVB   | 128 GB | 2       | 383   | 0     | 1.05   |
| Samsung   | MZ7TE128HMGR-00000 | 128 GB | 2       | 382   | 0     | 1.05   |
| Kingston  | SM2280S3G2240G     | 240 GB | 2       | 380   | 0     | 1.04   |
| Samsung   | SSD 840 EVO        | 1 TB   | 4       | 375   | 0     | 1.03   |
| Samsung   | MZMPC032HBCD-00000 | 32 GB  | 5       | 372   | 0     | 1.02   |
| OCZ       | VERTEX3 MI         | 120 GB | 15      | 452   | 134   | 1.02   |
| OCZ       | VERTEX4            | 256 GB | 11      | 542   | 1     | 1.02   |
| Samsung   | MZ7TD256HAFV-000L7 | 256 GB | 2       | 370   | 0     | 1.02   |
| Samsung   | SSD 850 EVO mSATA  | 120 GB | 2       | 369   | 0     | 1.01   |
| Toshiba   | THNSNC128GCSJ      | 128 GB | 1       | 367   | 0     | 1.01   |
| Plextor   | PX-64M3            | 64 GB  | 3       | 668   | 346   | 1.00   |
| OCZ       | VERTEX3            | 90 GB  | 11      | 678   | 7     | 0.99   |
| Samsung   | MZMPC128HBFU-000H1 | 128 GB | 1       | 361   | 0     | 0.99   |
| KingShare | 230120SSD          | 128 GB | 1       | 358   | 0     | 0.98   |
| Kingston  | SH103S3120G        | 120 GB | 36      | 358   | 0     | 0.98   |
| Samsung   | SSD 840 EVO        | 120 GB | 43      | 356   | 0     | 0.98   |
| SanDisk   | SDSSDH2128G        | 128 GB | 1       | 356   | 0     | 0.98   |
| KingFast  | SSD                | 256 GB | 3       | 355   | 0     | 0.97   |
| KingSpec  | KSD-SA25.5-016MJ   | 16 GB  | 1       | 353   | 0     | 0.97   |
| BHT       | WR202HH032G E70... | 31 GB  | 1       | 351   | 0     | 0.96   |
| SPCC      | SSD110             | 120 GB | 4       | 459   | 254   | 0.96   |
| Samsung   | SSD 850 PRO        | 128 GB | 16      | 349   | 0     | 0.96   |
| Plextor   | PX-128M3           | 128 GB | 2       | 349   | 0     | 0.96   |
| Toshiba   | THNSNX024GMNT      | 24 GB  | 2       | 346   | 0     | 0.95   |
| Samsung   | SSD 840 EVO        | 500 GB | 12      | 346   | 0     | 0.95   |
| Kingston  | SVP200S37A60G      | 64 GB  | 6       | 345   | 0     | 0.95   |
| Advantech | SQF-S25M4-32G-S9E  | 32 GB  | 1       | 345   | 0     | 0.95   |
| SanDisk   | SDSSDHII480G       | 480 GB | 4       | 344   | 0     | 0.95   |
| Samsung   | MZ7TD128HAFV-000L1 | 128 GB | 1       | 340   | 0     | 0.93   |
| Intel     | SSDSCKJW120H6      | 120 GB | 1       | 339   | 0     | 0.93   |
| Toshiba   | THNS064GE4BBDC     | 64 GB  | 1       | 338   | 0     | 0.93   |
| China     | SATA SSD           | 20 GB  | 7       | 383   | 1     | 0.93   |
| OCZ       | VERTEX4            | 64 GB  | 7       | 338   | 1     | 0.92   |
| KingFast  | SSD                | 32 GB  | 1       | 332   | 0     | 0.91   |
| OCZ       | VERTEX PLUS R2     | 128 GB | 2       | 331   | 0     | 0.91   |
| Intel     | SSDSA2M080G2GC     | 80 GB  | 5       | 716   | 3     | 0.91   |
| Crucial   | C300-CTFDDAC128MAG | 128 GB | 3       | 330   | 0     | 0.91   |
| Samsung   | SSD 830 Series     | 128 GB | 7       | 329   | 0     | 0.90   |
| Samsung   | MZMPC032HBCD-000H1 | 32 GB  | 5       | 325   | 0     | 0.89   |
| Samsung   | MZMTD256HAGM-000L1 | 256 GB | 2       | 325   | 0     | 0.89   |
| Apple     | SSD TS128C         | 121 GB | 2       | 323   | 0     | 0.89   |
| Apple     | SSD SM0512G        | 500 GB | 1       | 323   | 0     | 0.89   |
| Intel     | SSDSC2CT240A4      | 240 GB | 5       | 321   | 0     | 0.88   |
| OCZ       | VERTEX3 LP         | 64 GB  | 1       | 320   | 0     | 0.88   |
| Intel     | SSDSA2BW160G3L     | 160 GB | 3       | 320   | 0     | 0.88   |
| PNY       | SSD2SC240G1CS17... | 240 GB | 1       | 317   | 0     | 0.87   |
| SanDisk   | SDSSDHP064G        | 64 GB  | 8       | 316   | 0     | 0.87   |
| Crucial   | CT275MX300SSD4     | 275 GB | 1       | 316   | 0     | 0.87   |
| Intel     | SSDSC2BA200G4      | 200 GB | 5       | 313   | 0     | 0.86   |
| SanDisk   | Ultra II           | 960 GB | 3       | 502   | 1     | 0.86   |
| Goodram   | C50                | 64 GB  | 1       | 313   | 0     | 0.86   |
| OCZ       | AGILITY3           | 128 GB | 2       | 313   | 0     | 0.86   |
| Crucial   | C300-CTFDDAC064MAG | 64 GB  | 1       | 307   | 0     | 0.84   |
| Kingston  | SVP200S3240G       | 240 GB | 2       | 307   | 0     | 0.84   |
| Corsair   | Force 3 SSD        | 90 GB  | 4       | 307   | 0     | 0.84   |
| Toshiba   | THNSNC128GBSJ      | 128 GB | 1       | 303   | 0     | 0.83   |
| Samsung   | SSD PM830 2.5" 7mm | 128 GB | 1       | 302   | 0     | 0.83   |
| OCZ       | AGILITY2           | 64 GB  | 2       | 302   | 0     | 0.83   |
| SanDisk   | SDSSDX120GG25      | 120 GB | 4       | 301   | 0     | 0.83   |
| Samsung   | MZ7TD128HAFV-00000 | 128 GB | 1       | 300   | 0     | 0.82   |
| OCZ       | SOLID3             | 64 GB  | 2       | 558   | 7     | 0.82   |
| Mushkin   | MKNSSDAT240GB-DX   | 240 GB | 1       | 299   | 0     | 0.82   |
| Plextor   | PX-256M5Pro        | 256 GB | 4       | 298   | 0     | 0.82   |
| SanDisk   | SSD U100           | 128 GB | 6       | 390   | 33    | 0.81   |
| SanDisk   | X300 2.5 7MM       | 256 GB | 1       | 297   | 0     | 0.81   |
| Ramaxel   | RDM-II XM020C024G  | 24 GB  | 2       | 295   | 0     | 0.81   |
| Kingston  | SNVP325S2256GB     | 256 GB | 1       | 293   | 0     | 0.80   |
| OCZ       | VECTOR             | 128 GB | 3       | 296   | 5     | 0.80   |
| Samsung   | MZMPA064HMDR-00000 | 64 GB  | 1       | 290   | 0     | 0.79   |
| Intel     | SSDSC2BW180A4      | 180 GB | 7       | 370   | 2     | 0.79   |
| OCZ       | AGILITY3           | 90 GB  | 3       | 476   | 1     | 0.79   |
| OCZ       | CACHE-SYNAPSE      | 32 GB  | 1       | 286   | 0     | 0.79   |
| Kingston  | SH103S3240G        | 240 GB | 10      | 467   | 213   | 0.78   |
| Transcend | TS128GSSD340       | 128 GB | 4       | 283   | 0     | 0.78   |
| OCZ       | VERTEX             | 64 GB  | 1       | 280   | 0     | 0.77   |
| Kingston  | SKC300S37A120G     | 120 GB | 12      | 280   | 0     | 0.77   |
| Kingston  | SMS100S232G        | 32 GB  | 1       | 279   | 0     | 0.76   |
| PNY       | CS2211 480GB SSD   | 480 GB | 1       | 277   | 0     | 0.76   |
| ADATA     | SP900              | 256 GB | 8       | 371   | 2     | 0.75   |
| Samsung   | SSD 840 Series     | 250 GB | 8       | 275   | 0     | 0.75   |
| Kingston  | SMS200S360G        | 64 GB  | 8       | 282   | 1     | 0.75   |
| Intel     | SSDSC2BW180A3L     | 180 GB | 3       | 275   | 0     | 0.75   |
| Toshiba   | THNSNJ128G8NU      | 128 GB | 2       | 274   | 0     | 0.75   |
| SanDisk   | SD6SB1M128G1001    | 128 GB | 1       | 271   | 0     | 0.74   |
| SK hynix  | SH920 2.5 7MM      | 256 GB | 1       | 271   | 0     | 0.74   |
| Samsung   | MZNLN256HCHP-000L7 | 256 GB | 3       | 270   | 0     | 0.74   |
| SanDisk   | SDSSDHP128G        | 128 GB | 17      | 284   | 1     | 0.74   |
| Intel     | SSDSC2BP240G4      | 240 GB | 2       | 269   | 0     | 0.74   |
| Goodram   | GOODRAM SSD        | 120 GB | 2       | 269   | 0     | 0.74   |
| SanDisk   | SD8SN8U512G1002    | 512 GB | 3       | 268   | 0     | 0.74   |
| Samsung   | SSD 850 EVO        | 120 GB | 41      | 268   | 0     | 0.74   |
| Goodram   | GOODRAM C40        | 120 GB | 3       | 266   | 0     | 0.73   |
| SanDisk   | iSSD P4            | 8 GB   | 3       | 350   | 1     | 0.73   |
| SK hynix  | HFS120G32TND-N1A2A | 120 GB | 1       | 264   | 0     | 0.73   |
| Kingston  | SKC400S37128G      | 128 GB | 2       | 264   | 0     | 0.72   |
| Crucial   | CT240M500SSD1      | 240 GB | 12      | 475   | 184   | 0.72   |
| Toshiba   | TR150              | 120 GB | 3       | 263   | 0     | 0.72   |
| Apacer    | A7202              | 64 GB  | 1       | 262   | 0     | 0.72   |
| Samsung   | SSD PM830 mSATA    | 128 GB | 1       | 261   | 0     | 0.72   |
| Crucial   | CT500MX200SSD1     | 500 GB | 6       | 260   | 0     | 0.71   |
| Samsung   | MMCQE28GFMUP-MVA   | 128 GB | 2       | 298   | 13    | 0.71   |
| Samsung   | SSD PM810 TM       | 64 GB  | 1       | 257   | 0     | 0.70   |
| SanDisk   | SD6SB1M128G        | 128 GB | 1       | 256   | 0     | 0.70   |
| Corsair   | Force GS           | 240 GB | 3       | 1272  | 6     | 0.70   |
| Corsair   | Force GS           | 128 GB | 14      | 256   | 0     | 0.70   |
| Samsung   | MZ7TE256HMHP-000L7 | 256 GB | 2       | 255   | 0     | 0.70   |
| Kingston  | SKC300S37A60G      | 64 GB  | 12      | 373   | 6     | 0.70   |
| Micron    | 1100 SATA          | 512 GB | 1       | 253   | 0     | 0.69   |
| Samsung   | SSD 840 Series     | 500 GB | 2       | 392   | 1     | 0.69   |
| Crucial   | CT512MX100SSD1     | 512 GB | 6       | 252   | 0     | 0.69   |
| Samsung   | SSD PM800 TH       | 64 GB  | 1       | 251   | 0     | 0.69   |
| OCZ       | TRION150           | 240 GB | 3       | 249   | 0     | 0.68   |
| ADATA     | SX900              | 64 GB  | 3       | 500   | 339   | 0.68   |
| Kingston  | SV300S37A60G       | 64 GB  | 94      | 250   | 1     | 0.68   |
| ADATA     | SP900              | 128 GB | 22      | 319   | 16    | 0.68   |
| Intel     | SSDSA2M080G2HP     | 80 GB  | 1       | 245   | 0     | 0.67   |
| Plextor   | PX-128M7VC         | 128 GB | 5       | 245   | 0     | 0.67   |
| Intel     | SSDSA1MH080G1GN    | 80 GB  | 1       | 244   | 0     | 0.67   |
| Corsair   | CSSD-V64GB2        | 64 GB  | 1       | 243   | 0     | 0.67   |
| SanDisk   | SDSSDP064G         | 64 GB  | 5       | 294   | 205   | 0.66   |
| HP        | VK0240GDJXU        | 240 GB | 1       | 238   | 0     | 0.65   |
| Plextor   | PX-512M5P          | 512 GB | 1       | 238   | 0     | 0.65   |
| Crucial   | M4-CT128M4SSD3     | 128 GB | 1       | 238   | 0     | 0.65   |
| Crucial   | CT240M500SSD3      | 240 GB | 3       | 342   | 11    | 0.65   |
| Samsung   | MZNLF128HCHP-00000 | 128 GB | 2       | 233   | 0     | 0.64   |
| SanDisk   | SSD i100           | 16 GB  | 5       | 233   | 0     | 0.64   |
| Apacer    | AST680S            | 128 GB | 2       | 232   | 0     | 0.64   |
| SanDisk   | SDSSDH31000G       | 1 TB   | 1       | 231   | 0     | 0.64   |
| Patriot   | Blaze              | 240 GB | 2       | 231   | 0     | 0.63   |
| Crucial   | CT120M500SSD1      | 120 GB | 9       | 436   | 8     | 0.63   |
| Kingston  | SM2280S3120G       | 120 GB | 3       | 230   | 0     | 0.63   |
| Toshiba   | A100               | 240 GB | 2       | 230   | 0     | 0.63   |
| SanDisk   | Z400s M.2 2280     | 256 GB | 1       | 229   | 0     | 0.63   |
| Kingston  | SV100S264G         | 64 GB  | 6       | 391   | 4     | 0.63   |
| Samsung   | MZNTY256HDHP-000L7 | 256 GB | 1       | 228   | 0     | 0.63   |
| Samsung   | SSD 850 PRO        | 256 GB | 41      | 227   | 0     | 0.62   |
| Samsung   | SSD 840 Series     | 120 GB | 13      | 239   | 1     | 0.62   |
| OCZ       | OCTANE S2          | 64 GB  | 1       | 224   | 0     | 0.61   |
| Kingston  | SVP200S37A90G      | 90 GB  | 2       | 223   | 0     | 0.61   |
| Crucial   | CT500MX200SSD4     | 500 GB | 2       | 222   | 0     | 0.61   |
| SanDisk   | SD5SG2256G1052E    | 256 GB | 2       | 222   | 0     | 0.61   |
| Kingston  | SUV300S37A480G     | 480 GB | 1       | 222   | 0     | 0.61   |
| SanDisk   | SSD U110           | 64 GB  | 1       | 222   | 0     | 0.61   |
| Team      | L3 SSD             | 120 GB | 2       | 221   | 0     | 0.61   |
| Samsung   | SSD 860 EVO mSATA  | 1 TB   | 1       | 221   | 0     | 0.61   |
| Kingston  | SV100S232G         | 32 GB  | 3       | 219   | 0     | 0.60   |
| Samsung   | MZNTE128HMGR-000SO | 128 GB | 2       | 379   | 773   | 0.60   |
| Samsung   | MMDPE56GFDXP-MVB   | 256 GB | 1       | 218   | 0     | 0.60   |
| Kingston  | SV200S3256G        | 256 GB | 3       | 676   | 3     | 0.59   |
| Samsung   | SSD 850 EVO        | 250 GB | 114     | 215   | 0     | 0.59   |
| Goodram   | GOODRAM C100       | 120 GB | 1       | 214   | 0     | 0.59   |
| OCZ       | TRION100           | 240 GB | 6       | 213   | 0     | 0.59   |
| Kingston  | SV300S37A120G      | 120 GB | 270     | 252   | 22    | 0.58   |
| Samsung   | SSD 850 EVO        | 500 GB | 71      | 212   | 0     | 0.58   |
| Intel     | SSDSC2BB300G4      | 304 GB | 1       | 211   | 0     | 0.58   |
| WDC       | WDS500G1B0B-00AS40 | 500 GB | 1       | 210   | 0     | 0.58   |
| OCZ       | VECTOR150          | 120 GB | 9       | 210   | 0     | 0.58   |
| Toshiba   | THNSNJ128GCST      | 128 GB | 3       | 208   | 0     | 0.57   |
| SanDisk   | X400 M.2 2280      | 256 GB | 2       | 208   | 0     | 0.57   |
| OCZ       | VERTEX2            | 50 GB  | 2       | 309   | 320   | 0.57   |
| Palit     | PH120 SSD          | 120 GB | 1       | 207   | 0     | 0.57   |
| Toshiba   | THNSNH128GBST      | 128 GB | 2       | 207   | 0     | 0.57   |
| SanDisk   | SD8SN8U128G1002    | 128 GB | 1       | 206   | 0     | 0.57   |
| Goodram   | GOODRAM C50        | 64 GB  | 1       | 204   | 0     | 0.56   |
| SPCC      | SSD B29            | 32 GB  | 1       | 204   | 0     | 0.56   |
| ADATA     | SP600              | 128 GB | 3       | 203   | 0     | 0.56   |
| Smartbuy  | m.2 S11-2280S      | 128 GB | 1       | 202   | 0     | 0.56   |
| Toshiba   | THNSNJ128GCSU      | 128 GB | 3       | 202   | 0     | 0.56   |
| SanDisk   | X400 M.2 2280      | 128 GB | 1       | 202   | 0     | 0.56   |
| Samsung   | MZRPA128HMCD-000SO | 64 GB  | 10      | 202   | 0     | 0.56   |
| SanDisk   | SD7TB6S256G1001    | 256 GB | 1       | 200   | 0     | 0.55   |
| SanDisk   | SD5SF2128G1014E    | 128 GB | 2       | 200   | 0     | 0.55   |
| Samsung   | MZ7LN512HMJP-000L7 | 512 GB | 1       | 198   | 0     | 0.54   |
| OCZ       | VERTEX PLUS        | 64 GB  | 1       | 396   | 1     | 0.54   |
| SanDisk   | SD6SF1M128G1022I   | 128 GB | 1       | 396   | 1     | 0.54   |
| Samsung   | MZNTD256HAGL-00000 | 256 GB | 1       | 196   | 0     | 0.54   |
| Samsung   | MZNTY256HDHP-000L2 | 256 GB | 1       | 195   | 0     | 0.54   |
| Samsung   | MZMPC032HBCD-000L1 | 32 GB  | 1       | 195   | 0     | 0.53   |
| Plextor   | PX-128S3G          | 128 GB | 1       | 194   | 0     | 0.53   |
| OCZ       | ARC100             | 480 GB | 2       | 197   | 1     | 0.53   |
| OCZ       | VERTEX4            | 512 GB | 1       | 573   | 2     | 0.52   |
| Kingston  | RBU-SNS8152S312... | 128 GB | 2       | 190   | 0     | 0.52   |
| WDC       | WDS250G1B0A-00H9H0 | 250 GB | 6       | 190   | 0     | 0.52   |
| Kingston  | SS100S216G         | 16 GB  | 1       | 190   | 0     | 0.52   |
| Plextor   | PH6-CE120-G        | 120 GB | 1       | 189   | 0     | 0.52   |
| Toshiba   | THNSNJ256GCSU      | 256 GB | 3       | 188   | 0     | 0.52   |
| Kingston  | SV100S2128G        | 128 GB | 2       | 359   | 2     | 0.52   |
| Smartbuy  | SSD                | 120 GB | 52      | 188   | 0     | 0.52   |
| Samsung   | SG9MSM6D024GPM00   | 22 GB  | 1       | 188   | 0     | 0.52   |
| ADATA     | SP900              | 64 GB  | 12      | 249   | 2     | 0.51   |
| Transcend | TS128GSSD720       | 128 GB | 2       | 187   | 0     | 0.51   |
| Toshiba   | THNSNH128GMCT      | 128 GB | 2       | 186   | 0     | 0.51   |
| SPCC      | SSD162             | 120 GB | 7       | 406   | 436   | 0.51   |
| Smartbuy  | mSata              | 64 GB  | 1       | 186   | 0     | 0.51   |
| Crucial   | M4-CT512M4SSD2     | 512 GB | 1       | 184   | 0     | 0.51   |
| Intel     | SSDSC2CT180A4      | 180 GB | 5       | 184   | 0     | 0.50   |
| Crucial   | CT2000MX500SSD1    | 2 TB   | 1       | 183   | 0     | 0.50   |
| Patriot   | Spark              | 128 GB | 6       | 181   | 0     | 0.50   |
| Plextor   | PX-256M7VC         | 256 GB | 3       | 181   | 0     | 0.50   |
| Transcend | TS128GMSA740       | 128 GB | 1       | 180   | 0     | 0.50   |
| ADATA     | SX900              | 128 GB | 7       | 705   | 584   | 0.49   |
| SPCC      | SSD                | 128 GB | 4       | 179   | 0     | 0.49   |
| Crucial   | CT960M500SSD1      | 960 GB | 4       | 445   | 517   | 0.49   |
| SanDisk   | SDSSDHII120G       | 120 GB | 17      | 178   | 0     | 0.49   |
| ADATA     | SSD S599           | 64 GB  | 1       | 178   | 0     | 0.49   |
| Samsung   | SSD PM800 Serie... | 256 GB | 1       | 178   | 0     | 0.49   |
| SanDisk   | SD7SB3Q256G1002    | 256 GB | 1       | 355   | 1     | 0.49   |
| KingDian  | S400 XT            | 240 GB | 1       | 177   | 0     | 0.49   |
| Smartbuy  | SSD                | 64 GB  | 20      | 175   | 0     | 0.48   |
| PNY       | CS900 120GB SSD    | 120 GB | 1       | 175   | 0     | 0.48   |
| SanDisk   | SDSSDP128G         | 128 GB | 20      | 174   | 1     | 0.48   |
| SK hynix  | HFS256G32TND-N210A | 256 GB | 1       | 172   | 0     | 0.47   |
| Plextor   | PX-128M7VG         | 128 GB | 1       | 171   | 0     | 0.47   |
| China     | SSD                | 64 GB  | 5       | 210   | 1     | 0.47   |
| SanDisk   | SDSSDP256G         | 256 GB | 2       | 169   | 0     | 0.46   |
| Intel     | SSDSA2CT040G3      | 40 GB  | 3       | 167   | 0     | 0.46   |
| Kingston  | SUV400S37480G      | 480 GB | 1       | 164   | 0     | 0.45   |
| Corsair   | Force LE200 SSD    | 120 GB | 1       | 164   | 0     | 0.45   |
| SanDisk   | SD7SB6S256G1122    | 256 GB | 1       | 163   | 0     | 0.45   |
| Kingston  | SM2280S3G2120G     | 120 GB | 2       | 162   | 0     | 0.44   |
| Apacer    | 256GB SATA Flas... | 256 GB | 1       | 161   | 0     | 0.44   |
| Crucial   | M4-CT512M4SSD1     | 512 GB | 1       | 161   | 0     | 0.44   |
| Intel     | SSDSCMMW180A3L     | 180 GB | 1       | 160   | 0     | 0.44   |
| Samsung   | MZNLF128HCHP-00004 | 128 GB | 3       | 160   | 0     | 0.44   |
| Kingston  | SMS200S3120G       | 120 GB | 7       | 167   | 110   | 0.44   |
| Crucial   | CT250MX200SSD1     | 250 GB | 4       | 159   | 0     | 0.44   |
| Patriot   | Flare              | 64 GB  | 1       | 157   | 0     | 0.43   |
| SPCC      | SSD                | 64 GB  | 63      | 169   | 49    | 0.43   |
| Samsung   | MMCRE64GFMPP-MVA   | 64 GB  | 2       | 155   | 0     | 0.43   |
| Plextor   | PX-256S2C          | 256 GB | 2       | 153   | 0     | 0.42   |
| Samsung   | MZNLN128HCGR-000L2 | 128 GB | 1       | 153   | 0     | 0.42   |
| Samsung   | MZNTY128HDHP-000L1 | 128 GB | 1       | 153   | 0     | 0.42   |
| Samsung   | SSD 850 EVO M.2    | 250 GB | 8       | 153   | 0     | 0.42   |
| Samsung   | SSD 840 EVO 500... | 500 GB | 1       | 152   | 0     | 0.42   |
| Patriot   | Blast              | 120 GB | 4       | 152   | 0     | 0.42   |
| SanDisk   | SSD i100           | 24 GB  | 12      | 156   | 3     | 0.41   |
| OCZ       | ARC100             | 120 GB | 8       | 150   | 0     | 0.41   |
| SanDisk   | SDSSDX240GG25      | 240 GB | 1       | 1348  | 8     | 0.41   |
| China     | SATA SSD           | 128 GB | 4       | 149   | 0     | 0.41   |
| Samsung   | SSD 750 EVO        | 120 GB | 23      | 148   | 0     | 0.41   |
| Kingston  | SHSS37A120G        | 120 GB | 6       | 148   | 0     | 0.41   |
| Intel     | SSDMCEAC180B3      | 180 GB | 2       | 148   | 0     | 0.41   |
| Corsair   | Neutron GTX SSD    | 240 GB | 4       | 180   | 74    | 0.41   |
| Smartbuy  | m.2 S10-2280T      | 128 GB | 1       | 147   | 0     | 0.40   |
| SPCC      | SSD                | 120 GB | 90      | 182   | 114   | 0.40   |
| SanDisk   | SDSSDHII240G       | 240 GB | 9       | 146   | 0     | 0.40   |
| Samsung   | SSD 750 EVO        | 500 GB | 3       | 146   | 0     | 0.40   |
| Goodram   | GOODRAM CX100      | 120 GB | 6       | 152   | 2     | 0.40   |
| Samsung   | MZMPA024HMCD-000L1 | 24 GB  | 2       | 198   | 10    | 0.40   |
| Intel     | SSDSC2BB120G4      | 120 GB | 1       | 143   | 0     | 0.39   |
| QUMO      | SSD                | 64 GB  | 1       | 143   | 0     | 0.39   |
| Patriot   | Blast              | 240 GB | 4       | 143   | 0     | 0.39   |
| Corsair   | CSSD-F60GB2        | 64 GB  | 3       | 1108  | 246   | 0.39   |
| KingSpec  | KSD-SA25.5-064MJ   | 64 GB  | 1       | 141   | 0     | 0.39   |
| Intel     | SSDSC2BW240H6      | 240 GB | 3       | 139   | 0     | 0.38   |
| Team      | L3 EVO SSD         | 120 GB | 2       | 139   | 0     | 0.38   |
| ADATA     | SX930              | 120 GB | 1       | 138   | 0     | 0.38   |
| Crucial   | CT750MX300SSD1     | 752 GB | 4       | 137   | 0     | 0.38   |
| Intel     | SSDSC2BB080G4      | 80 GB  | 1       | 135   | 0     | 0.37   |
| SanDisk   | SDSSDHP256G        | 256 GB | 5       | 135   | 0     | 0.37   |
| Kingston  | SV300S37A240G      | 240 GB | 52      | 135   | 1     | 0.37   |
| SK hynix  | HFS128G32MND-3210A | 128 GB | 1       | 135   | 0     | 0.37   |
| Transcend | TS256GMTS400       | 256 GB | 3       | 132   | 0     | 0.36   |
| Kingston  | SMS200S330G        | 32 GB  | 1       | 132   | 0     | 0.36   |
| OCZ       | AGILITY4           | 256 GB | 4       | 142   | 61    | 0.36   |
| Toshiba   | THNSNF064GMCS      | 64 GB  | 2       | 129   | 0     | 0.35   |
| Samsung   | MZMTD128HAFV-000L1 | 128 GB | 7       | 153   | 21    | 0.35   |
| SanDisk   | SDSSDXPS240G       | 240 GB | 4       | 136   | 259   | 0.35   |
| ADATA     | SP600              | 32 GB  | 4       | 127   | 0     | 0.35   |
| OCZ       | VECTOR150          | 240 GB | 2       | 127   | 0     | 0.35   |
| Goodram   | GOODRAM            | 120 GB | 17      | 126   | 0     | 0.35   |
| Plextor   | PX-128M5S          | 128 GB | 40      | 128   | 1     | 0.35   |
| Chiprex   | S10T3120GB         | 120 GB | 1       | 126   | 0     | 0.35   |
| Apple     | SSD TS256C         | 256 GB | 2       | 126   | 0     | 0.35   |
| KingFast  | SSD                | 29 GB  | 1       | 125   | 0     | 0.34   |
| Crucial   | CT256M550SSD1      | 256 GB | 5       | 378   | 7     | 0.34   |
| Samsung   | SSD 750 EVO        | 250 GB | 15      | 124   | 0     | 0.34   |
| Kingston  | SUV400S37240G      | 240 GB | 39      | 131   | 27    | 0.34   |
| OCZ       | ARC100             | 240 GB | 5       | 123   | 0     | 0.34   |
| Apple     | SSD SM512E         | 500 GB | 1       | 123   | 0     | 0.34   |
| OCZ       | VERTEX450          | 128 GB | 1       | 121   | 0     | 0.33   |
| Toshiba   | VX500              | 256 GB | 1       | 120   | 0     | 0.33   |
| ADATA     | SSD S511           | 64 GB  | 3       | 450   | 679   | 0.33   |
| Samsung   | SSD 850 EVO M.2    | 500 GB | 7       | 120   | 0     | 0.33   |
| ADATA     | SP310              | 128 GB | 1       | 120   | 0     | 0.33   |
| KingDian  | S400               | 120 GB | 6       | 120   | 0     | 0.33   |
| Kingston  | RBU-SNS8152S312... | 128 GB | 1       | 120   | 0     | 0.33   |
| ADATA     | SSD SX900 512GB... | 512 GB | 1       | 120   | 0     | 0.33   |
| Kingston  | SHSS37A480G        | 480 GB | 5       | 119   | 0     | 0.33   |
| Apacer    | AS340              | 120 GB | 1       | 119   | 0     | 0.33   |
| Kingston  | SUV300S37A240G     | 240 GB | 7       | 118   | 0     | 0.32   |
| ADATA     | XM13               | 32 GB  | 1       | 116   | 0     | 0.32   |
| Crucial   | CT1024MX200SSD1    | 1 TB   | 1       | 116   | 0     | 0.32   |
| Kingston  | SVP200S3120G       | 120 GB | 4       | 370   | 499   | 0.32   |
| Samsung   | MZMPC128HBFU-000   | 128 GB | 1       | 114   | 0     | 0.31   |
| Corsair   | Force LE SSD       | 120 GB | 2       | 114   | 0     | 0.31   |
| OCZ       | TRION100           | 120 GB | 4       | 141   | 3     | 0.31   |
| OCZ       | D2CSTK181M11-0180  | 180 GB | 3       | 114   | 0     | 0.31   |
| Transcend | TS128GMTS400S      | 128 GB | 1       | 113   | 0     | 0.31   |
| OCZ       | VERTEX2            | 90 GB  | 1       | 113   | 0     | 0.31   |
| Micron    | MTFDDAK512MAM-1K1  | 512 GB | 1       | 113   | 0     | 0.31   |
| Crucial   | CT240BX300SSD1     | 240 GB | 1       | 113   | 0     | 0.31   |
| Toshiba   | Q300               | 120 GB | 2       | 112   | 0     | 0.31   |
| Kingston  | RBUSNS8280S3128GH2 | 128 GB | 2       | 112   | 0     | 0.31   |
| Kingston  | SUV300S37A120G     | 120 GB | 18      | 112   | 0     | 0.31   |
| Samsung   | MZNLN256HMHQ-000H1 | 256 GB | 2       | 112   | 0     | 0.31   |
| SanDisk   | SD6SB1M128G1002    | 128 GB | 1       | 110   | 0     | 0.30   |
| Team      | L5 LITE SSD        | 120 GB | 2       | 110   | 0     | 0.30   |
| Intenso   | SSD                | 128 GB | 3       | 219   | 1     | 0.30   |
| ADATA     | SP920SS            | 128 GB | 4       | 306   | 4     | 0.30   |
| Samsung   | MZNLF128HCHP-000H1 | 128 GB | 1       | 109   | 0     | 0.30   |
| SanDisk   | Ultra II           | 480 GB | 2       | 109   | 0     | 0.30   |
| SanDisk   | SD8TN8U256G1001    | 256 GB | 1       | 109   | 0     | 0.30   |
| SanDisk   | SD7SB6S-128G-1006  | 128 GB | 1       | 108   | 0     | 0.30   |
| Crucial   | CT512M550SSD3      | 512 GB | 2       | 109   | 193   | 0.30   |
| Mushkin   | MKNSSDRE1TB        | 1 TB   | 1       | 107   | 0     | 0.30   |
| Lite-On   | IT L8T-128L9G      | 128 GB | 1       | 105   | 0     | 0.29   |
| Smartbuy  | SSD                | 240 GB | 13      | 120   | 1     | 0.29   |
| SanDisk   | SSD U100           | 16 GB  | 1       | 105   | 0     | 0.29   |
| Toshiba   | TR200              | 480 GB | 2       | 104   | 0     | 0.29   |
| Samsung   | MZ7PD256HCGM-000H7 | 256 GB | 1       | 104   | 0     | 0.29   |
| Samsung   | MZNTD128HAGM-00000 | 128 GB | 2       | 104   | 0     | 0.29   |
| ADATA     | SP600              | 64 GB  | 7       | 113   | 2     | 0.28   |
| Plextor   | PX-128M5M          | 128 GB | 7       | 103   | 0     | 0.28   |
| Lite-On   | CV5-8Q128          | 128 GB | 1       | 103   | 0     | 0.28   |
| Transcend | TS120GSSD25D-M     | 128 GB | 1       | 309   | 2     | 0.28   |
| Samsung   | SSD 860 EVO M.2    | 1 TB   | 1       | 102   | 0     | 0.28   |
| Toshiba   | THNSNH256GBST      | 256 GB | 1       | 102   | 0     | 0.28   |
| Smartbuy  | mSata              | 256 GB | 1       | 102   | 0     | 0.28   |
| KingFast  | SSD                | 32 GB  | 1       | 102   | 0     | 0.28   |
| SanDisk   | Ultra II           | 240 GB | 6       | 100   | 0     | 0.28   |
| OCZ       | VERTEX460          | 120 GB | 2       | 363   | 9     | 0.27   |
| Samsung   | MZ7LN512HCHP-000L1 | 512 GB | 1       | 99    | 0     | 0.27   |
| Kingston  | SKC400S37512G      | 512 GB | 1       | 99    | 0     | 0.27   |
| Toshiba   | THNSNJ128G8NY      | 128 GB | 1       | 98    | 0     | 0.27   |
| SanDisk   | SD8SN8U512G1122    | 512 GB | 1       | 98    | 0     | 0.27   |
| SPCC      | SSD A20            | 64 GB  | 1       | 97    | 0     | 0.27   |
| Intenso   | SSD                | 120 GB | 1       | 97    | 0     | 0.27   |
| Anobit    | Gen2A400 118032738 | 400 GB | 1       | 96    | 0     | 0.27   |
| SanDisk   | SD7SB3Q128G1002    | 128 GB | 1       | 387   | 3     | 0.27   |
| Toshiba   | THNSNJ512GDNU A    | 512 GB | 1       | 96    | 0     | 0.26   |
| SPCC      | SSD170             | 120 GB | 3       | 245   | 341   | 0.26   |
| Corsair   | Force LS SSD       | 120 GB | 8       | 212   | 505   | 0.26   |
| WDC       | WDS250G1B0B-00AS40 | 250 GB | 3       | 94    | 0     | 0.26   |
| SanDisk   | SSD U100           | 256 GB | 1       | 94    | 0     | 0.26   |
| Patriot   | Blaze              | 64 GB  | 4       | 94    | 0     | 0.26   |
| Intel     | SSDSC2BW120A4      | 120 GB | 22      | 104   | 1     | 0.26   |
| Lite-On   | PH2-CJ120          | 120 GB | 1       | 92    | 0     | 0.25   |
| OCZ       | VERTEX460A         | 120 GB | 4       | 92    | 0     | 0.25   |
| Kingston  | SUV400S37120G      | 120 GB | 41      | 105   | 9     | 0.25   |
| Plextor   | PX-256M5S          | 256 GB | 9       | 91    | 0     | 0.25   |
| Faspeed   | H5-60G PLUS        | 64 GB  | 1       | 90    | 0     | 0.25   |
| Kingston  | RBU-SNS8151S396GG  | 96 GB  | 1       | 88    | 0     | 0.24   |
| Samsung   | MZ7LN256HCHP-000L7 | 256 GB | 2       | 87    | 0     | 0.24   |
| Plextor   | PX-128M5Pro        | 128 GB | 50      | 87    | 0     | 0.24   |
| Kingston  | SKC380S3120G       | 120 GB | 1       | 86    | 0     | 0.24   |
| Mushkin   | MKNSSDEC120GB      | 120 GB | 1       | 86    | 0     | 0.24   |
| WDC       | WDBNCE2500PNC      | 250 GB | 1       | 85    | 0     | 0.23   |
| SK hynix  | SC311 SATA         | 512 GB | 2       | 85    | 0     | 0.23   |
| Plextor   | PX-256M3           | 256 GB | 1       | 256   | 2     | 0.23   |
| SanDisk   | SD7SN3Q128G1002    | 128 GB | 1       | 85    | 0     | 0.23   |
| Kingmax   | SSD                | 120 GB | 17      | 195   | 421   | 0.23   |
| PNY       | CS1311 240GB SSD   | 240 GB | 1       | 84    | 0     | 0.23   |
| Transcend | TS256GSSD320       | 256 GB | 2       | 84    | 0     | 0.23   |
| Apple     | SSD SM0256G        | 256 GB | 1       | 83    | 0     | 0.23   |
| Samsung   | SSD 840 EVO 250... | 250 GB | 3       | 83    | 0     | 0.23   |
| Kingston  | SV300S37A480G      | 480 GB | 7       | 91    | 144   | 0.23   |
| Apple     | SSD TS064C         | 60 GB  | 1       | 81    | 0     | 0.22   |
| OCZ       | VECTOR180          | 120 GB | 2       | 81    | 0     | 0.22   |
| Intel     | SSDSA2M160G2LE     | 160 GB | 1       | 1872  | 22    | 0.22   |
| Corsair   | Force LS SSD       | 480 GB | 1       | 80    | 0     | 0.22   |
| Kingston  | RBU-SNS8152S325... | 256 GB | 1       | 80    | 0     | 0.22   |
| SK hynix  | SC308 SATA         | 128 GB | 2       | 80    | 0     | 0.22   |
| Lite-On   | LAT-256M2S         | 256 GB | 1       | 239   | 2     | 0.22   |
| Fordisk   | S860 256G 6Gbps    | 256 GB | 1       | 79    | 0     | 0.22   |
| Seagate   | ST120HM000-1G5142  | 120 GB | 1       | 79    | 0     | 0.22   |
| Toshiba   | Q300 Pro           | 128 GB | 1       | 79    | 0     | 0.22   |
| ADATA     | SU650              | 480 GB | 1       | 77    | 0     | 0.21   |
| SanDisk   | SSD i100           | 8 GB   | 2       | 77    | 0     | 0.21   |
| Corsair   | Neutron XTI SSD    | 240 GB | 1       | 77    | 0     | 0.21   |
| Kingston  | SHSS37A240G        | 240 GB | 12      | 77    | 0     | 0.21   |
| Transcend | TS256GSSD340       | 256 GB | 2       | 76    | 0     | 0.21   |
| China     | SATA SSD           | 64 GB  | 10      | 76    | 0     | 0.21   |
| Samsung   | SSD 650            | 120 GB | 3       | 75    | 0     | 0.21   |
| Corsair   | Neutron SSD        | 64 GB  | 2       | 174   | 6     | 0.21   |
| Intel     | SSDSC2BW240A4      | 240 GB | 7       | 74    | 0     | 0.21   |
| OCZ       | ONYX               | 32 GB  | 2       | 105   | 1     | 0.21   |
| ADATA     | SP580              | 120 GB | 6       | 74    | 0     | 0.20   |
| Lite-On   | CV3-8D128-11 SATA  | 128 GB | 2       | 73    | 0     | 0.20   |
| KingDian  | S400               | 480 GB | 1       | 73    | 0     | 0.20   |
| WDC       | WDS500G2B0A-00SM50 | 500 GB | 3       | 72    | 0     | 0.20   |
| SanDisk   | SD8SB8U256G1122    | 256 GB | 2       | 72    | 0     | 0.20   |
| Crucial   | CT128M550SSD3      | 128 GB | 3       | 212   | 11    | 0.20   |
| SPCC      | SSD                | 55 GB  | 7       | 236   | 436   | 0.20   |
| OCZ       | VERTEX460A         | 240 GB | 2       | 71    | 0     | 0.19   |
| Crucial   | CT525MX300SSD1     | 528 GB | 5       | 77    | 4     | 0.19   |
| Kingston  | SS200S330G         | 32 GB  | 1       | 70    | 0     | 0.19   |
| OCZ       | SABER1000          | 480 GB | 1       | 70    | 0     | 0.19   |
| Toshiba   | TR150              | 480 GB | 2       | 70    | 0     | 0.19   |
| PNY       | CS1311 120GB SSD   | 120 GB | 3       | 69    | 0     | 0.19   |
| Transcend | TS256GMTS800       | 256 GB | 2       | 69    | 0     | 0.19   |
| China     | 64GB SSD           | 64 GB  | 10      | 68    | 0     | 0.19   |
| SanDisk   | SD5SE2256G1002E    | 256 GB | 1       | 68    | 0     | 0.19   |
| SanDisk   | PLUS               | 480 GB | 2       | 68    | 0     | 0.19   |
| Kingston  | SHFS37A240G        | 240 GB | 12      | 96    | 424   | 0.19   |
| Intel     | SSDSC2BW120H6      | 120 GB | 7       | 68    | 0     | 0.19   |
| Samsung   | MZNTY256HDHP-000H1 | 256 GB | 1       | 204   | 2     | 0.19   |
| WDC       | WDS240G1G0A-00SS50 | 240 GB | 8       | 68    | 0     | 0.19   |
| ADATA     | S596               | 128 GB | 1       | 68    | 0     | 0.19   |
| SK hynix  | SC308 SATA         | 256 GB | 2       | 67    | 0     | 0.19   |
| Plextor   | PX-128M6M          | 128 GB | 4       | 67    | 0     | 0.19   |
| Toshiba   | TR150              | 240 GB | 7       | 67    | 0     | 0.19   |
| PNY       | SSD2SC240G1LC70... | 240 GB | 1       | 67    | 0     | 0.18   |
| WDC       | WDS500G1B0A-00H9H0 | 500 GB | 3       | 67    | 0     | 0.18   |
| ADATA     | SP900              | 512 GB | 2       | 66    | 0     | 0.18   |
| Samsung   | SSD 860 EVO M.2    | 500 GB | 1       | 66    | 0     | 0.18   |
| SanDisk   | SD8TB8U512G1001    | 512 GB | 1       | 66    | 0     | 0.18   |
| China     | 128GB SSD          | 128 GB | 5       | 66    | 0     | 0.18   |
| Kingston  | RBU-SNS8100S3256GD | 256 GB | 1       | 66    | 0     | 0.18   |
| Corsair   | Force LS SSD       | 64 GB  | 16      | 202   | 195   | 0.18   |
| Corsair   | CSSD-F120GB3-BK    | 120 GB | 1       | 65    | 0     | 0.18   |
| SPCC      | SSD                | 240 GB | 26      | 156   | 340   | 0.18   |
| Intel     | SSDSC2BW480A4      | 480 GB | 1       | 65    | 0     | 0.18   |
| Lite-On   | LMT-32L3M-HP       | 32 GB  | 2       | 65    | 0     | 0.18   |
| Transcend | TS64GMSA370        | 64 GB  | 2       | 65    | 0     | 0.18   |
| Corsair   | Force LE200 SSD    | 240 GB | 1       | 64    | 0     | 0.18   |
| WDC       | WDS250G2B0B-00YS70 | 250 GB | 1       | 64    | 0     | 0.18   |
| Intel     | SSDSA2M160G2GC     | 160 GB | 1       | 578   | 8     | 0.18   |
| KingSpec  | NT-256             | 256 GB | 3       | 64    | 0     | 0.18   |
| Apple     | SSD SM0128G        | 121 GB | 1       | 64    | 0     | 0.18   |
| Kingston  | SKC400S37256G      | 256 GB | 1       | 64    | 0     | 0.18   |
| WDC       | WDS240G1G0B-00RC30 | 240 GB | 4       | 63    | 0     | 0.17   |
| Intel     | SSDSC2BW080A4      | 80 GB  | 1       | 63    | 0     | 0.17   |
| Transcend | TS128GSSD370       | 128 GB | 6       | 63    | 0     | 0.17   |
| KingSpec  | Q-180              | 180 GB | 2       | 63    | 0     | 0.17   |
| SanDisk   | SSD U110           | 16 GB  | 9       | 63    | 0     | 0.17   |
| Crucial   | CT128M550SSD1      | 128 GB | 3       | 88    | 30    | 0.17   |
| China     | 120GB SSD          | 120 GB | 25      | 62    | 0     | 0.17   |
| Toshiba   | Q200 EX            | 240 GB | 1       | 61    | 0     | 0.17   |
| SanDisk   | SDSSDA240G         | 240 GB | 40      | 61    | 0     | 0.17   |
| Plextor   | PX-128M6S          | 128 GB | 22      | 66    | 51    | 0.17   |
| PHISON    | 128GB PS3109-S9    | 128 GB | 1       | 121   | 1     | 0.17   |
| SanDisk   | SSD U100           | 24 GB  | 15      | 70    | 19    | 0.17   |
| Samsung   | MZNLN256HCHP-00000 | 256 GB | 1       | 60    | 0     | 0.17   |
| Kingston  | SHPM2280P2H-480G   | 480 GB | 1       | 180   | 2     | 0.16   |
| Goodram   | GOODRAM IR-SSDP... | 120 GB | 2       | 59    | 0     | 0.16   |
| Plextor   | PX-256M6S          | 256 GB | 8       | 63    | 127   | 0.16   |
| Patriot   | Burst              | 480 GB | 3       | 59    | 0     | 0.16   |
| Micron    | 1100_MTFDDAV512TBN | 512 GB | 4       | 59    | 0     | 0.16   |
| TEKET     | SA18-032M-4F       | 32 GB  | 2       | 59    | 0     | 0.16   |
| OCZ       | VERTEX2            | 180 GB | 1       | 58    | 0     | 0.16   |
| Toshiba   | THNSNK128GVN8      | 128 GB | 2       | 58    | 0     | 0.16   |
| Plextor   | PX-512M6Pro        | 512 GB | 1       | 58    | 0     | 0.16   |
| SanDisk   | SDSSDH2064G        | 64 GB  | 1       | 58    | 0     | 0.16   |
| Goldkey   | GKH84-64GB         | 64 GB  | 1       | 57    | 0     | 0.16   |
| Kingston  | SUV500480G         | 480 GB | 1       | 57    | 0     | 0.16   |
| ADATA     | SP610              | 128 GB | 2       | 57    | 0     | 0.16   |
| ADATA     | SP900NS38          | 128 GB | 3       | 124   | 339   | 0.16   |
| Samsung   | MZNTY256HDHP-00000 | 256 GB | 2       | 56    | 0     | 0.16   |
| OCZ       | VERTEX460          | 240 GB | 1       | 56    | 0     | 0.15   |
| Radeon    | R7                 | 120 GB | 1       | 56    | 0     | 0.15   |
| Samsung   | SSD 860 EVO M.2    | 250 GB | 5       | 55    | 0     | 0.15   |
| Samsung   | SSD 860 EVO        | 1 TB   | 7       | 55    | 0     | 0.15   |
| Kingston  | SHFS37A120G        | 120 GB | 52      | 131   | 412   | 0.15   |
| Samsung   | SSD 860 EVO        | 500 GB | 17      | 55    | 0     | 0.15   |
| Transcend | TS64GSSD340        | 64 GB  | 1       | 54    | 0     | 0.15   |
| Crucial   | CT250BX100SSD1     | 250 GB | 4       | 54    | 0     | 0.15   |
| China     | SSD 120G           | 120 GB | 2       | 54    | 0     | 0.15   |
| Lite-On   | L8H-256V2G-HP      | 256 GB | 2       | 54    | 0     | 0.15   |
| AMD       | R5SL240G           | 240 GB | 2       | 54    | 0     | 0.15   |
| SanDisk   | SSD PLUS 240 GB    | 240 GB | 5       | 53    | 0     | 0.15   |
| Samsung   | MZMTD128HAFV-000H1 | 128 GB | 1       | 53    | 0     | 0.15   |
| Zheino    | CHN-25SATAA3-480   | 480 GB | 2       | 53    | 0     | 0.15   |
| Samsung   | MZMPC128HBFU-000MV | 128 GB | 1       | 53    | 0     | 0.15   |
| SanDisk   | SDSSDA960G         | 960 GB | 1       | 52    | 0     | 0.14   |
| Team      | L5 LITE SSD        | 64 GB  | 1       | 52    | 0     | 0.14   |
| Intel     | SSDSC2BB240G4      | 240 GB | 1       | 52    | 0     | 0.14   |
| Team      | L7 EVO SSD         | 64 GB  | 1       | 51    | 0     | 0.14   |
| Lite-On   | LMT-64M6M-HP       | 64 GB  | 1       | 51    | 0     | 0.14   |
| Lite-On   | LMT-19nmBGA-128G   | 128 GB | 1       | 51    | 0     | 0.14   |
| Lite-On   | CV3-8D128          | 128 GB | 2       | 50    | 0     | 0.14   |
| Samsung   | MZMTD128HAFV-000   | 128 GB | 3       | 50    | 0     | 0.14   |
| Mushkin   | MKNSSDSR250GB      | 250 GB | 1       | 50    | 0     | 0.14   |
| Samsung   | SSD PB22-CS3 FD... | 256 GB | 1       | 50    | 0     | 0.14   |
| OCZ       | INTREPID 3800      | 400 GB | 1       | 50    | 0     | 0.14   |
| Samsung   | MZ7LF128HCHP-00004 | 128 GB | 1       | 50    | 0     | 0.14   |
| Kingston  | SA400S37240G       | 240 GB | 26      | 67    | 5     | 0.14   |
| Corsair   | Neutron GTX SSD    | 480 GB | 1       | 49    | 0     | 0.14   |
| KingDian  | S200               | 120 GB | 2       | 49    | 0     | 0.13   |
| Samsung   | MZNTY128HDHP-00000 | 128 GB | 2       | 48    | 0     | 0.13   |
| Transcend | TS256GSSD230S      | 256 GB | 1       | 48    | 0     | 0.13   |
| SK hynix  | HFS128G32MND-3212A | 128 GB | 1       | 48    | 0     | 0.13   |
| Plextor   | PX-128S3C          | 128 GB | 8       | 47    | 0     | 0.13   |
| GeIL      | R3 120G            | 120 GB | 1       | 47    | 0     | 0.13   |
| China     | 80GB SSD           | 80 GB  | 2       | 47    | 0     | 0.13   |
| Micron    | 1100_MTFDDAK256TBN | 256 GB | 4       | 47    | 0     | 0.13   |
| SPCC      | M.2 SSD            | 120 GB | 3       | 107   | 2     | 0.13   |
| Plextor   | PX-256M8VG         | 256 GB | 1       | 46    | 0     | 0.13   |
| oyunkey   | SSD                | 120 GB | 1       | 46    | 0     | 0.13   |
| Micron    | 1100_MTFDDAV256TBN | 256 GB | 7       | 51    | 242   | 0.13   |
| SanDisk   | SD5SF2032G1010E    | 32 GB  | 1       | 45    | 0     | 0.13   |
| Crucial   | CT275MX300SSD1     | 275 GB | 10      | 45    | 1     | 0.13   |
| Samsung   | SSD 860 EVO        | 250 GB | 27      | 45    | 0     | 0.13   |
| Crucial   | CT1000MX500SSD1    | 1 TB   | 2       | 45    | 0     | 0.12   |
| Kingston  | RBU-SC152S37128GG2 | 128 GB | 1       | 45    | 0     | 0.12   |
| Plextor   | PX-256M5M          | 256 GB | 1       | 45    | 0     | 0.12   |
| Goodram   | GOODRAM IR-SSDP... | 240 GB | 1       | 44    | 0     | 0.12   |
| PRETEC    | G2000 SSD          | 29 GB  | 1       | 44    | 0     | 0.12   |
| ADATA     | SU700              | 120 GB | 3       | 44    | 0     | 0.12   |
| Plextor   | PX-512M3           | 512 GB | 1       | 1402  | 31    | 0.12   |
| WDC       | WDS120G1G0A-00SS50 | 120 GB | 14      | 43    | 0     | 0.12   |
| KingDian  | S280-240GB         | 240 GB | 7       | 43    | 0     | 0.12   |
| China     | SSD128G            | 128 GB | 1       | 42    | 0     | 0.12   |
| KingSpec  | T-64               | 64 GB  | 2       | 59    | 3     | 0.12   |
| China     | 240GB SSD          | 240 GB | 1       | 41    | 0     | 0.11   |
| ADATA     | SP920SS            | 256 GB | 4       | 138   | 8     | 0.11   |
| China     | SATA SSD           | 120 GB | 11      | 39    | 0     | 0.11   |
| ADATA     | SP550              | 240 GB | 6       | 39    | 0     | 0.11   |
| WDC       | WDS100T1B0A-00H9H0 | 1 TB   | 2       | 39    | 0     | 0.11   |
| Kingston  | SA400S37120G       | 120 GB | 68      | 40    | 1     | 0.11   |
| Apacer    | AS330              | 120 GB | 2       | 39    | 0     | 0.11   |
| WDC       | WDS120G2G0B-00EPW0 | 120 GB | 1       | 78    | 1     | 0.11   |
| Plextor   | PX-AG128M6e        | 128 GB | 3       | 186   | 2     | 0.11   |
| WDC       | WDS250G2B0A-00SM50 | 250 GB | 2       | 38    | 0     | 0.11   |
| Kingston  | SH103S3480G        | 480 GB | 1       | 38    | 0     | 0.11   |
| Kingston  | RBUSNS8180S3128GI1 | 128 GB | 1       | 38    | 0     | 0.11   |
| SanDisk   | SDSSDH3512G        | 512 GB | 1       | 38    | 0     | 0.10   |
| Intel     | SSDSC2KW256G8      | 256 GB | 9       | 37    | 0     | 0.10   |
| Samsung   | SSD 850 EVO mSATA  | 250 GB | 2       | 37    | 0     | 0.10   |
| Crucial   | CT120BX300SSD1     | 120 GB | 2       | 37    | 0     | 0.10   |
| SanDisk   | SD6SB1M128G1022I   | 128 GB | 2       | 37    | 0     | 0.10   |
| SanDisk   | SSD PLUS 120 GB    | 120 GB | 7       | 37    | 0     | 0.10   |
| Samsung   | MZNTY128HDHP-000H1 | 128 GB | 2       | 37    | 0     | 0.10   |
| WDC       | WDS240G2G0A-00JH30 | 240 GB | 12      | 37    | 0     | 0.10   |
| Corsair   | CSSD-V60GB2        | 64 GB  | 1       | 332   | 8     | 0.10   |
| Crucial   | CT120BX500SSD1     | 120 GB | 10      | 36    | 0     | 0.10   |
| Micron    | MTFDDAK512MAY-1... | 512 GB | 1       | 624   | 16    | 0.10   |
| Intel     | SSDSA1M080G2HP     | 80 GB  | 1       | 476   | 12    | 0.10   |
| Transcend | TS256GMTS430S      | 256 GB | 2       | 36    | 0     | 0.10   |
| AMD       | R3SL60G            | 64 GB  | 2       | 35    | 0     | 0.10   |
| PNY       | CS900 240GB SSD    | 240 GB | 2       | 35    | 0     | 0.10   |
| Samsung   | MZNLN128HAHQ-00000 | 128 GB | 1       | 35    | 0     | 0.10   |
| Plextor   | PX-256S3C          | 256 GB | 1       | 34    | 0     | 0.10   |
| Plextor   | PX-64M5M           | 64 GB  | 1       | 34    | 0     | 0.10   |
| Patriot   | Burst              | 240 GB | 3       | 34    | 0     | 0.10   |
| ZOTAC     | SATA SSD           | 120 GB | 2       | 34    | 0     | 0.09   |
| China     | SATA SSD           | 240 GB | 5       | 34    | 0     | 0.09   |
| AMD       | R3SL120G           | 120 GB | 19      | 34    | 0     | 0.09   |
| ADATA     | SX950              | 240 GB | 1       | 34    | 0     | 0.09   |
| AMD       | R5S240GBSF         | 240 GB | 1       | 33    | 0     | 0.09   |
| AMD       | R5SL120G           | 120 GB | 7       | 53    | 1     | 0.09   |
| Intel     | SSDSA1MH080G1HP    | 80 GB  | 1       | 33    | 0     | 0.09   |
| KingDian  | S180               | 64 GB  | 10      | 38    | 114   | 0.09   |
| SanDisk   | SD6SB1M-032G-1006  | 32 GB  | 1       | 33    | 0     | 0.09   |
| Plextor   | PX-128M6Pro        | 128 GB | 8       | 32    | 0     | 0.09   |
| China     | SSD                | 120 GB | 4       | 32    | 0     | 0.09   |
| Smartbuy  | mSata              | 128 GB | 2       | 32    | 0     | 0.09   |
| SPCC      | SSD                | 256 GB | 4       | 72    | 26    | 0.09   |
| Kingmax   | SSD                | 64 GB  | 18      | 223   | 524   | 0.09   |
| Samsung   | SSD PM851          | 128 GB | 1       | 32    | 0     | 0.09   |
| KingSpec  | ACSC4M512mSA       | 506 GB | 1       | 32    | 0     | 0.09   |
| OCZ       | VERTEX4            | 79 GB  | 1       | 129   | 3     | 0.09   |
| Lite-On   | L8T-128L6G-HP      | 128 GB | 2       | 32    | 640   | 0.09   |
| SanDisk   | SDSSDXP120G        | 120 GB | 1       | 32    | 0     | 0.09   |
| Micron    | C400-MTFDDAK256MAM | 256 GB | 1       | 32    | 0     | 0.09   |
| Toshiba   | THNSNB062GMCJ      | 64 GB  | 1       | 32    | 0     | 0.09   |
| KingSpec  | Q-360              | 360 GB | 2       | 31    | 0     | 0.09   |
| Samsung   | MZMTD512HAGL-000L1 | 512 GB | 2       | 84    | 49    | 0.09   |
| Samsung   | SSD 850            | 120 GB | 17      | 31    | 0     | 0.09   |
| SanDisk   | SDSSDA480G         | 480 GB | 3       | 31    | 0     | 0.09   |
| OCZ       | TRION150           | 480 GB | 1       | 31    | 0     | 0.09   |
| KingSpec  | KSD-SA25.7-016MJ   | 16 GB  | 2       | 30    | 0     | 0.08   |
| Toshiba   | VT180              | 480 GB | 1       | 30    | 0     | 0.08   |
| SanDisk   | SSD i100           | 32 GB  | 2       | 30    | 0     | 0.08   |
| ADATA     | SP900NS34          | 128 GB | 1       | 30    | 0     | 0.08   |
| Micron    | MTFDDAK256MAM-1K12 | 256 GB | 3       | 71    | 1010  | 0.08   |
| Samsung   | MZ7LN256HAJQ-00000 | 256 GB | 1       | 30    | 0     | 0.08   |
| PNY       | SSD2SC120G1CS17... | 120 GB | 2       | 30    | 0     | 0.08   |
| SanDisk   | SSD PLUS           | 240 GB | 4       | 30    | 0     | 0.08   |
| SanDisk   | SDSSDA120G         | 120 GB | 27      | 33    | 4     | 0.08   |
| SK hynix  | HFS128G39MNC-3510A | 128 GB | 1       | 30    | 0     | 0.08   |
| Micron    | MTFDDAK128MAM-1J1  | 128 GB | 1       | 29    | 0     | 0.08   |
| SanDisk   | SDSA5DK-016G-1006  | 16 GB  | 1       | 29    | 0     | 0.08   |
| KingPower | 1108 SSD           | 64 GB  | 1       | 29    | 0     | 0.08   |
| Apple     | SSD SD0128F        | 121 GB | 1       | 29    | 0     | 0.08   |
| Samsung   | MZ7TY256HDHP-00000 | 256 GB | 1       | 29    | 0     | 0.08   |
| Transcend | TS128GSSD370S      | 128 GB | 14      | 29    | 0     | 0.08   |
| ADATA     | SU800NS38          | 256 GB | 1       | 29    | 0     | 0.08   |
| Intel     | SSDSA1M160G2HP     | 160 GB | 3       | 90    | 5     | 0.08   |
| SK hynix  | HFS128G39TND-N210A | 128 GB | 9       | 29    | 0     | 0.08   |
| Samsung   | SSD Thin uSATA ... | 128 GB | 1       | 378   | 12    | 0.08   |
| Kingston  | RBUSNS8180S3128GJ  | 128 GB | 1       | 29    | 0     | 0.08   |
| Transcend | TS128GMTS400       | 128 GB | 1       | 29    | 0     | 0.08   |
| KingSpec  | MT-128             | 128 GB | 4       | 29    | 0     | 0.08   |
| Patriot   | Spark              | 256 GB | 2       | 28    | 0     | 0.08   |
| ADATA     | SU800              | 128 GB | 18      | 30    | 5     | 0.08   |
| Samsung   | SSD 860 EVO        | 2 TB   | 3       | 28    | 0     | 0.08   |
| Toshiba   | THNSNF256GMCS      | 256 GB | 1       | 28    | 0     | 0.08   |
| Crucial   | CT500MX500SSD4     | 500 GB | 2       | 28    | 0     | 0.08   |
| LDLC      | SSD                | 120 GB | 2       | 27    | 0     | 0.08   |
| Toshiba   | TR200              | 240 GB | 9       | 27    | 0     | 0.08   |
| Samsung   | MZ7TY128HDHP-000L1 | 128 GB | 2       | 27    | 0     | 0.08   |
| SenDisk   | C3-60G             | 64 GB  | 1       | 27    | 0     | 0.08   |
| Team      | TEAML5Lite3D120G   | 120 GB | 1       | 27    | 0     | 0.07   |
| KingSpec  | CHA-M2B7-M256      | 256 GB | 2       | 27    | 0     | 0.07   |
| Transcend | TS64GSSD720        | 64 GB  | 1       | 26    | 0     | 0.07   |
| Transcend | TS64GSSD320        | 64 GB  | 1       | 26    | 0     | 0.07   |
| Intel     | SSDSC2BB240G7      | 240 GB | 2       | 25    | 0     | 0.07   |
| KingSpec  | T-120              | 120 GB | 1       | 25    | 0     | 0.07   |
| SK hynix  | HFS512G39TNF-N3A0A | 512 GB | 1       | 25    | 0     | 0.07   |
| Toshiba   | THNSNH128G8NT      | 128 GB | 1       | 25    | 0     | 0.07   |
| Plextor   | PX-512M5Pro        | 512 GB | 1       | 25    | 0     | 0.07   |
| Apacer    | AS350              | 120 GB | 4       | 25    | 0     | 0.07   |
| Crucial   | CT480BX500SSD1     | 480 GB | 2       | 25    | 0     | 0.07   |
| Intel     | SSDSC2BW180A3H     | 180 GB | 1       | 25    | 0     | 0.07   |
| SK hynix  | HFS256G32MND-2900A | 256 GB | 1       | 531   | 20    | 0.07   |
| Transcend | TS240GSSD220S      | 240 GB | 4       | 25    | 0     | 0.07   |
| Lite-On   | CV5-8Q256          | 256 GB | 1       | 24    | 0     | 0.07   |
| Corsair   | CSSD-V32GB2        | 32 GB  | 1       | 99    | 3     | 0.07   |
| Kingston  | SA400S37480G       | 480 GB | 9       | 30    | 10    | 0.07   |
| Plextor   | PX-128S2C          | 128 GB | 2       | 24    | 0     | 0.07   |
| Toshiba   | Q300               | 480 GB | 1       | 24    | 0     | 0.07   |
| ADATA     | SU650              | 120 GB | 7       | 34    | 2     | 0.07   |
| PNY       | SSD2SC120G1SA75... | 120 GB | 1       | 23    | 0     | 0.07   |
| Crucial   | CT250MX500SSD1     | 250 GB | 3       | 23    | 0     | 0.06   |
| Londisk   | SSD                | 120 GB | 3       | 23    | 0     | 0.06   |
| Intel     | SSDSA2BW160G3H     | 160 GB | 2       | 98    | 4     | 0.06   |
| Apacer    | AS350              | 240 GB | 5       | 23    | 0     | 0.06   |
| Transcend | TS256GSSD370S      | 256 GB | 2       | 23    | 0     | 0.06   |
| Kingrich  | SSD 120G           | 120 GB | 1       | 23    | 0     | 0.06   |
| GLOWAY    | FER240GS3-S7       | 240 GB | 1       | 23    | 0     | 0.06   |
| Toshiba   | THNSNS060GBSP      | 64 GB  | 1       | 22    | 0     | 0.06   |
| Plextor   | PX-128M6V          | 128 GB | 1       | 22    | 0     | 0.06   |
| Kingston  | SKC300S37A180G     | 180 GB | 2       | 166   | 1025  | 0.06   |
| e2e4      | SSD                | 120 GB | 2       | 22    | 0     | 0.06   |
| Lite-On   | CV3-DE256          | 256 GB | 2       | 22    | 0     | 0.06   |
| Plextor   | PX-256M6M          | 256 GB | 3       | 29    | 1     | 0.06   |
| Plextor   | PX-256M8VC         | 256 GB | 1       | 21    | 0     | 0.06   |
| OCZ       | INTREPID 3600      | 400 GB | 1       | 21    | 0     | 0.06   |
| Transcend | TS120GSSD220S      | 120 GB | 5       | 21    | 0     | 0.06   |
| Samsung   | SSD 860 EVO mSATA  | 250 GB | 5       | 21    | 0     | 0.06   |
| Lite-On   | CV1-8B128          | 128 GB | 3       | 21    | 0     | 0.06   |
| Transcend | TS128GSSD230S      | 128 GB | 6       | 20    | 0     | 0.06   |
| ADATA     | SU900              | 256 GB | 4       | 21    | 1     | 0.06   |
| Goldkey   | GKH84-256GB        | 256 GB | 1       | 20    | 0     | 0.06   |
| KingDian  | S280               | 240 GB | 7       | 20    | 0     | 0.06   |
| Lenovo    | SSD SL700 480G     | 480 GB | 1       | 20    | 0     | 0.06   |
| AMD       | R3SL240G           | 240 GB | 4       | 44    | 1     | 0.06   |
| KingDian  | S280               | 120 GB | 4       | 20    | 0     | 0.06   |
| XUNZHE    | XUNZHE XUNZHE80... | 120 GB | 1       | 20    | 0     | 0.05   |
| Samsung   | MZYLF128HCHP-000L2 | 128 GB | 1       | 20    | 0     | 0.05   |
| Netac     | SSD 120G           | 120 GB | 1       | 19    | 0     | 0.05   |
| Intel     | SSDSCKGF256A5 SATA | 256 GB | 1       | 19    | 0     | 0.05   |
| Transcend | TS128GMTS800       | 128 GB | 3       | 19    | 0     | 0.05   |
| SanDisk   | SD8SN8U-128G-1006  | 128 GB | 10      | 40    | 3     | 0.05   |
| Kingston  | SUV500120G         | 120 GB | 4       | 18    | 0     | 0.05   |
| SanDisk   | SSD U100           | 64 GB  | 5       | 18    | 0     | 0.05   |
| SanDisk   | SDSSDH3250G        | 250 GB | 1       | 18    | 0     | 0.05   |
| SK hynix  | SC210 2.5 7MM      | 128 GB | 1       | 18    | 0     | 0.05   |
| Seagate   | BarraCuda SSD Z... | 1 TB   | 1       | 18    | 0     | 0.05   |
| Corsair   | Neutron SSD        | 240 GB | 1       | 2126  | 114   | 0.05   |
| ADATA     | SP610              | 256 GB | 1       | 18    | 0     | 0.05   |
| Hyperdisk | SDOM               | 16 GB  | 1       | 18    | 0     | 0.05   |
| SK hynix  | HFS256G39TND-N210A | 256 GB | 2       | 18    | 0     | 0.05   |
| SanDisk   | SD8SN8U1T001122    | 1 TB   | 1       | 17    | 0     | 0.05   |
| China     | 60GB SSD           | 64 GB  | 1       | 17    | 0     | 0.05   |
| China     | RTMMB256VBV4KFY    | 256 GB | 1       | 17    | 0     | 0.05   |
| China     | SSD                | 240 GB | 6       | 36    | 1     | 0.05   |
| Kingrich  | 64GB K9 SATA3 SSD  | 63 GB  | 2       | 17    | 0     | 0.05   |
| AMD       | R3S60GBSM          | 64 GB  | 2       | 17    | 0     | 0.05   |
| LDNDISK   | SSD                | 240 GB | 1       | 16    | 0     | 0.05   |
| SanDisk   | SD6SB1M-128G-1006  | 128 GB | 1       | 16    | 0     | 0.05   |
| Platinet  | SSD                | 120 GB | 1       | 16    | 0     | 0.04   |
| Intel     | SSDSA2M080G2GN     | 80 GB  | 1       | 245   | 14    | 0.04   |
| Intel     | SSDMCEAW080A4      | 80 GB  | 1       | 16    | 0     | 0.04   |
| China     | SSD                | 128 GB | 4       | 16    | 0     | 0.04   |
| KingFast  | SSD                | 128 GB | 8       | 15    | 0     | 0.04   |
| Apple     | SSD SM256E         | 256 GB | 1       | 15    | 0     | 0.04   |
| Plextor   | PX-256M6Pro        | 256 GB | 1       | 15    | 0     | 0.04   |
| SanDisk   | SD8SBAT128G1122    | 128 GB | 1       | 15    | 0     | 0.04   |
| FASTDISK  | FASTDISK FASTDI... | 120 GB | 1       | 15    | 0     | 0.04   |
| GLOWAY    | FER120GS3-S7       | 120 GB | 2       | 15    | 0     | 0.04   |
| Samsung   | SSD 860 PRO        | 512 GB | 6       | 15    | 0     | 0.04   |
| WDC       | WDS120G2G0A-00JH30 | 120 GB | 22      | 15    | 0     | 0.04   |
| Transcend | TS32GSSD370S       | 32 GB  | 4       | 15    | 0     | 0.04   |
| Apacer    | AS510S             | 64 GB  | 2       | 15    | 0     | 0.04   |
| FORESEE   | 240GB SSD          | 240 GB | 1       | 15    | 0     | 0.04   |
| Crucial   | CT2050MX300SSD1    | 2 TB   | 2       | 29    | 1     | 0.04   |
| Transcend | TS64GSSD25S-M      | 64 GB  | 2       | 15    | 0     | 0.04   |
| SPCC      | SSD                | 480 GB | 1       | 15    | 0     | 0.04   |
| Samsung   | SSD 850 EVO mSATA  | 500 GB | 3       | 14    | 0     | 0.04   |
| FASTDISK  | FASTDISK 60G       | 64 GB  | 1       | 14    | 0     | 0.04   |
| Crucial   | CT240BX200SSD1     | 240 GB | 3       | 14    | 0     | 0.04   |
| Goodram   | GOODRAM SSDPR-C... | 128 GB | 2       | 14    | 0     | 0.04   |
| Seagate   | ST480FP0021        | 480 GB | 1       | 14    | 0     | 0.04   |
| QUMO      | SSD                | 120 GB | 2       | 303   | 509   | 0.04   |
| Apple     | SSD TS128E         | 121 GB | 1       | 128   | 8     | 0.04   |
| Micron    | M600_MTFDDAK1T0MBF | 1 TB   | 1       | 13    | 0     | 0.04   |
| ADATA     | SU800              | 1 TB   | 1       | 13    | 0     | 0.04   |
| Transcend | TS128GSSD360S      | 128 GB | 6       | 13    | 0     | 0.04   |
| OCZ       | VECTOR180          | 960 GB | 1       | 13    | 0     | 0.04   |
| Samsung   | MZYTY128HDHP-000L2 | 128 GB | 1       | 13    | 0     | 0.04   |
| Samsung   | SSD 860 QVO        | 1 TB   | 1       | 13    | 0     | 0.04   |
| FORESEE   | 64GB SSD           | 64 GB  | 2       | 13    | 0     | 0.04   |
| BIWIN     | SSD                | 120 GB | 1       | 13    | 0     | 0.04   |
| KingSpec  | P3-256             | 256 GB | 2       | 13    | 0     | 0.04   |
| Transcend | TS128GMTS600       | 128 GB | 1       | 13    | 0     | 0.04   |
| TCSUNBOW  | X3                 | 120 GB | 1       | 13    | 0     | 0.04   |
| SanDisk   | SSD PLUS           | 120 GB | 3       | 12    | 0     | 0.04   |
| SK hynix  | SH920 mSATA        | 256 GB | 1       | 680   | 52    | 0.04   |
| Transcend | TS512GMSA370       | 512 GB | 1       | 12    | 0     | 0.03   |
| SanDisk   | SSD P4             | 32 GB  | 9       | 92    | 134   | 0.03   |
| Crucial   | CT500MX500SSD1     | 500 GB | 6       | 12    | 0     | 0.03   |
| KingSpec  | P3-512             | 512 GB | 4       | 30    | 197   | 0.03   |
| China     | SSD                | 480 GB | 2       | 11    | 0     | 0.03   |
| HP        | SSD S700           | 250 GB | 1       | 11    | 0     | 0.03   |
| ADATA     | IM2S3138E-128GM-B  | 128 GB | 1       | 11    | 0     | 0.03   |
| Goodram   | GOODRAM SSDPR-C... | 120 GB | 1       | 11    | 0     | 0.03   |
| Crucial   | V4-CT128V4SSD2     | 128 GB | 1       | 11    | 0     | 0.03   |
| Faspeed   | M3-360G            | 360 GB | 1       | 11    | 0     | 0.03   |
| Crucial   | CT480BX200SSD1     | 480 GB | 2       | 11    | 0     | 0.03   |
| ADATA     | SP550              | 120 GB | 18      | 12    | 1     | 0.03   |
| Team      | T2535T120G         | 120 GB | 1       | 11    | 0     | 0.03   |
| Micron    | M600_MTFDDAV512MBF | 512 GB | 1       | 10    | 0     | 0.03   |
| Intel     | SSDSCKKW240H6      | 240 GB | 3       | 18    | 1     | 0.03   |
| ADATA     | SU650              | 240 GB | 6       | 10    | 0     | 0.03   |
| ADATA     | SX300              | 128 GB | 1       | 10    | 0     | 0.03   |
| Crucial   | CT240BX500SSD1     | 240 GB | 4       | 10    | 0     | 0.03   |
| Plextor   | PX-AG256M6e        | 256 GB | 1       | 10    | 0     | 0.03   |
| Lite-On   | LCH-256V2S-11 2... | 256 GB | 1       | 10    | 0     | 0.03   |
| Intel     | SSDSA2CW160G3      | 160 GB | 1       | 10    | 0     | 0.03   |
| Samsung   | SSD 860 QVO        | 2 TB   | 1       | 10    | 0     | 0.03   |
| KingSpec  | P3-128             | 128 GB | 2       | 9     | 0     | 0.03   |
| Toshiba   | TL100              | 240 GB | 2       | 9     | 0     | 0.03   |
| Crucial   | CT480M500SSD1      | 480 GB | 1       | 166   | 16    | 0.03   |
| SPCC      | SSD162             | 240 GB | 1       | 203   | 20    | 0.03   |
| LDLC      | SSD                | 128 GB | 3       | 9     | 0     | 0.03   |
| Faspeed   | H5-120G PLUS       | 120 GB | 1       | 9     | 0     | 0.03   |
| KingFast  | SSD                | 120 GB | 4       | 9     | 0     | 0.03   |
| KingSpec  | ACSC2M064mSA       | 63 GB  | 1       | 9     | 0     | 0.03   |
| KingDian  | S280-120GB         | 120 GB | 2       | 9     | 0     | 0.03   |
| Patriot   | Blaze              | 120 GB | 3       | 9     | 0     | 0.03   |
| ADATA     | SU900              | 128 GB | 1       | 9     | 0     | 0.02   |
| Intel     | SSDMCEAW180A4      | 180 GB | 1       | 9     | 0     | 0.02   |
| KingDian  | S280               | 480 GB | 1       | 9     | 0     | 0.02   |
| SK hynix  | HFS128G3BTND-N210A | 128 GB | 1       | 9     | 0     | 0.02   |
| Londisk   | SSD                | 240 GB | 1       | 8     | 0     | 0.02   |
| Teclast   | 128GB MS550        | 128 GB | 1       | 8     | 0     | 0.02   |
| KingDian  | N400 60G           | 64 GB  | 1       | 8     | 0     | 0.02   |
| SanDisk   | SD7SN6S-128G-1006  | 128 GB | 1       | 8     | 0     | 0.02   |
| SPCC      | SSD                | 512 GB | 2       | 8     | 0     | 0.02   |
| Londisk   | SSD                | 480 GB | 1       | 8     | 0     | 0.02   |
| WDC       | WDS240G2G0B-00EPW0 | 240 GB | 4       | 8     | 0     | 0.02   |
| Kingston  | RBU-SNS8100S312... | 128 GB | 2       | 8     | 0     | 0.02   |
| Plextor   | PH6-CE120          | 120 GB | 1       | 8     | 0     | 0.02   |
| PNY       | SSD2SC256GM1P3D... | 256 GB | 1       | 7     | 0     | 0.02   |
| Lite-On   | CV1-8B256          | 256 GB | 3       | 7     | 0     | 0.02   |
| FASTDISK  | FASTDISK 120G      | 120 GB | 1       | 7     | 0     | 0.02   |
| SK hynix  | SC311 SATA         | 128 GB | 3       | 7     | 0     | 0.02   |
| Apacer    | AST280             | 240 GB | 1       | 7     | 0     | 0.02   |
| SanDisk   | SD8SNAT256G1002    | 256 GB | 2       | 7     | 0     | 0.02   |
| KingSpec  | T-60               | 64 GB  | 3       | 7     | 0     | 0.02   |
| KingSpec  | ACSC2M128mSA       | 128 GB | 1       | 7     | 0     | 0.02   |
| Toshiba   | THNSNS128GMCP      | 128 GB | 1       | 7     | 0     | 0.02   |
| Zheino    | CHN 25SATA01M 060  | 64 GB  | 1       | 6     | 0     | 0.02   |
| KingDian  | S200               | 64 GB  | 4       | 6     | 0     | 0.02   |
| Intel     | SSDSCKJW180H6      | 180 GB | 1       | 6     | 0     | 0.02   |
| Patriot   | Ignite             | 240 GB | 1       | 6     | 0     | 0.02   |
| SanDisk   | SD8SBAT256G1122    | 256 GB | 3       | 6     | 0     | 0.02   |
| Transcend | TS240GMTS820S      | 240 GB | 1       | 6     | 0     | 0.02   |
| Samsung   | SSD PM871b 2.5 7mm | 128 GB | 1       | 6     | 0     | 0.02   |
| Integral  | V Series SATA SSD  | 240 GB | 1       | 6     | 0     | 0.02   |
| SK hynix  | SC210 mSATA        | 128 GB | 2       | 123   | 32    | 0.02   |
| Lite-On   | CV5-8Q512-HP       | 512 GB | 1       | 6     | 0     | 0.02   |
| Toshiba   | A100               | 120 GB | 2       | 6     | 0     | 0.02   |
| SK hynix  | SC210 mSATA        | 256 GB | 2       | 195   | 28    | 0.02   |
| Goodram   | GOODRAM SSDPR_C... | 120 GB | 1       | 6     | 0     | 0.02   |
| Samsung   | SSD 860 PRO        | 256 GB | 4       | 6     | 0     | 0.02   |
| Intel     | SSDSCKKF256G8 SATA | 256 GB | 1       | 6     | 0     | 0.02   |
| Patriot   | Burst              | 120 GB | 6       | 6     | 0     | 0.02   |
| Lite-On   | L8H-256V2G-11 M... | 256 GB | 1       | 6     | 0     | 0.02   |
| Smartbuy  | SSD                | 240 GB | 1       | 6     | 0     | 0.02   |
| GeIL      | Zenith A3-PRO      | 240 GB | 1       | 6     | 0     | 0.02   |
| GeIL      | Zenith A3          | 120 GB | 1       | 6     | 0     | 0.02   |
| Plextor   | PX-G256M6e         | 256 GB | 1       | 5     | 0     | 0.02   |
| Samsung   | SSD 860 QVO        | 4 TB   | 1       | 5     | 0     | 0.02   |
| ADATA     | SU800              | 256 GB | 2       | 37    | 6     | 0.02   |
| Dell      | WR202KD128G E70... | 128 GB | 1       | 5     | 0     | 0.02   |
| BIWIN     | SSD                | 128 GB | 2       | 5     | 0     | 0.02   |
| SanDisk   | SD8SNAT128G1002    | 128 GB | 2       | 5     | 0     | 0.02   |
| BIWIN     | G2242              | 64 GB  | 1       | 5     | 0     | 0.01   |
| Intel     | SSDSC2KW128G8      | 128 GB | 2       | 5     | 0     | 0.01   |
| KingSpec  | MT-256             | 256 GB | 2       | 5     | 0     | 0.01   |
| Vaseky    | V800-128G          | 128 GB | 1       | 5     | 0     | 0.01   |
| Drevo     | X1 SSD             | 120 GB | 2       | 314   | 34    | 0.01   |
| MicroData | MD500 120G         | 120 GB | 1       | 5     | 0     | 0.01   |
| Mushkin   | MKNSSDCG480GB      | 480 GB | 2       | 116   | 508   | 0.01   |
| Smartbuy  | m.2 S11-2280       | 128 GB | 1       | 4     | 0     | 0.01   |
| KingSpec  | ACSC2M128S25       | 128 GB | 1       | 4     | 0     | 0.01   |
| GeIL      | ZENITH R3_120GB    | 120 GB | 2       | 4     | 0     | 0.01   |
| Samsung   | SSD 850 EVO M.2    | 1 TB   | 1       | 4     | 0     | 0.01   |
| SanDisk   | SD8SB8U512G1122    | 512 GB | 1       | 4     | 0     | 0.01   |
| Transcend | TS64GSSD370        | 64 GB  | 2       | 4     | 0     | 0.01   |
| Crucial   | CT525MX300SSD4     | 528 GB | 1       | 4     | 0     | 0.01   |
| Corsair   | Neutron GTX SSD    | 128 GB | 1       | 1173  | 291   | 0.01   |
| GeIL      | ZENITH-A3 120G     | 120 GB | 1       | 3     | 0     | 0.01   |
| Intenso   | SSD Sata III       | 256 GB | 1       | 3     | 0     | 0.01   |
| Intel     | SSDSA1M080G2LE     | 80 GB  | 1       | 121   | 31    | 0.01   |
| Samsung   | MZ7LN128HAHQ-000L1 | 128 GB | 1       | 3     | 0     | 0.01   |
| SanDisk   | SATAIII            | 16 GB  | 1       | 3     | 0     | 0.01   |
| Crucial   | CT512M550SSD1      | 512 GB | 1       | 63    | 16    | 0.01   |
| KingSpec  | ACJC2M032mSH       | 32 GB  | 1       | 3     | 0     | 0.01   |
| WDC       | WDS100T2B0A-00SM50 | 1 TB   | 1       | 3     | 0     | 0.01   |
| Toshiba   | Q300               | 240 GB | 1       | 32    | 8     | 0.01   |
| FORESEE   | 128GB SSD          | 128 GB | 2       | 3     | 0     | 0.01   |
| Intel     | SSDSC2KW512G8      | 512 GB | 1       | 3     | 0     | 0.01   |
| OCZ       | REVODRIVE X2       | 64 GB  | 4       | 1204  | 516   | 0.01   |
| SPCC      | SSDB27             | 32 GB  | 1       | 23    | 6     | 0.01   |
| ShineDisk | M667 128G          | 120 GB | 1       | 3     | 0     | 0.01   |
| i-Flas... | K8                 | 63 GB  | 1       | 3     | 0     | 0.01   |
| Apacer    | 16GB SATA Flash... | 16 GB  | 1       | 33    | 10    | 0.01   |
| Gigabyte  | GP-GSTFS31120GNTD  | 120 GB | 1       | 3     | 0     | 0.01   |
| Transcend | TS256GSSD360S      | 256 GB | 2       | 2     | 0     | 0.01   |
| Samsung   | MZ7LN256HMJP-000H1 | 256 GB | 2       | 2     | 0     | 0.01   |
| Goodram   | GOODRAM IR_SSDP... | 120 GB | 1       | 2     | 0     | 0.01   |
| SanDisk   | SSD i110           | 128 GB | 1       | 2     | 0     | 0.01   |
| Dell      | WR202KD032G E70... | 31 GB  | 1       | 2     | 0     | 0.01   |
| Samsung   | SSD 860 EVO mSATA  | 500 GB | 1       | 2     | 0     | 0.01   |
| Fordisk   | SATA SSD           | 120 GB | 1       | 2     | 0     | 0.01   |
| Kingch... | SSD                | 64 GB  | 1       | 2     | 0     | 0.01   |
| KingSpec  | NT-512             | 512 GB | 1       | 24    | 8     | 0.01   |
| Dell      | WR202KD032G E70... | 31 GB  | 1       | 2     | 0     | 0.01   |
| Samsung   | MZNLN512HCJH-000H1 | 512 GB | 1       | 2     | 0     | 0.01   |
| SanDisk   | SDSA5GK-016G-1006  | 16 GB  | 1       | 276   | 106   | 0.01   |
| Gigastone | SS6200-256GB       | 256 GB | 1       | 2     | 0     | 0.01   |
| Intel     | SSDSC2KW240H6      | 240 GB | 2       | 14    | 6     | 0.01   |
| SanDisk   | SSD i110           | 16 GB  | 2       | 2     | 0     | 0.01   |
| SanDisk   | SSD i110           | 24 GB  | 1       | 2     | 0     | 0.01   |
| Transcend | TS64GMTS800        | 64 GB  | 1       | 2     | 0     | 0.01   |
| OCZ       | VERTEX3 LP         | 240 GB | 1       | 2268  | 1019  | 0.01   |
| ACPI      | M2SCF-6M           | 63 GB  | 1       | 2     | 0     | 0.01   |
| SK hynix  | SH920 2.5 7MM      | 128 GB | 1       | 54    | 25    | 0.01   |
| Seagate   | BarraCuda SSD Z... | 2 TB   | 1       | 2     | 0     | 0.01   |
| SanDisk   | SDSSDH120GG25      | 120 GB | 1       | 112   | 55    | 0.01   |
| Goodram   | GOODRAM SSDPR-C... | 240 GB | 1       | 2     | 0     | 0.01   |
| Lenovo    | SSD SL700 120G     | 120 GB | 1       | 2     | 0     | 0.01   |
| China     | SSD60G             | 64 GB  | 2       | 1     | 0     | 0.01   |
| Intel     | SSDSC2BP480G4      | 480 GB | 1       | 1     | 0     | 0.01   |
| Transcend | TS32GMSA370        | 32 GB  | 1       | 1     | 0     | 0.01   |
| Gigabyte  | GP-GSTFS31240GNTD  | 240 GB | 2       | 1     | 0     | 0.01   |
| Kingston  | SKC300S37A240G     | 240 GB | 2       | 1     | 0     | 0.01   |
| Golden... | GDSA25-120MS       | 120 GB | 1       | 1     | 0     | 0.01   |
| KingSpec  | P3D-240            | 240 GB | 1       | 1     | 0     | 0.01   |
| FASTDISK  | FASTDISK           | 64 GB  | 1       | 1     | 0     | 0.00   |
| Samsung   | MZNLN256HAJQ-000H1 | 256 GB | 1       | 174   | 100   | 0.00   |
| FASTDISK  | FASTDISK 30G       | 32 GB  | 1       | 1     | 0     | 0.00   |
| OCZ       | VERTEX2            | 100 GB | 1       | 1     | 0     | 0.00   |
| KingSpec  | ACJC2M064S25       | 63 GB  | 1       | 1     | 0     | 0.00   |
| Micron    | C400-MTFDDAT064MAM | 64 GB  | 1       | 1     | 0     | 0.00   |
| Intel     | SSDSC2KI128G8      | 128 GB | 1       | 1     | 0     | 0.00   |
| China     | SSD 256G           | 256 GB | 1       | 1     | 0     | 0.00   |
| SanDisk   | SD8SB8U128G1001    | 128 GB | 1       | 1     | 0     | 0.00   |
| Goodram   | GOODRAM SSDPR-C... | 120 GB | 1       | 1     | 0     | 0.00   |
| Samsung   | SSD 850 EVO mSATA  | 1 TB   | 1       | 1     | 0     | 0.00   |
| SK hynix  | HFS256G32MND-2200A | 256 GB | 1       | 225   | 153   | 0.00   |
| Samsung   | MZ7LF120HCHP-000L1 | 120 GB | 1       | 1     | 0     | 0.00   |
| Plextor   | PX-512M6M          | 512 GB | 1       | 1     | 0     | 0.00   |
| SanDisk   | SD8SNAT256G1122    | 256 GB | 1       | 1     | 0     | 0.00   |
| Samsung   | MZNLN128HAHQ-000L2 | 128 GB | 1       | 1     | 0     | 0.00   |
| Lite-On   | CV8-8E128-11 SATA  | 128 GB | 1       | 1     | 0     | 0.00   |
| Team      | M8PS5 SSD          | 128 GB | 1       | 1     | 0     | 0.00   |
| Kingston  | RBUSNS8180DS3256GJ | 256 GB | 1       | 1     | 0     | 0.00   |
| Zheino    | CHN25SATAS1 032    | 31 GB  | 2       | 1     | 0     | 0.00   |
| KingSpec  | ACJC2M128S25       | 128 GB | 1       | 1     | 0     | 0.00   |
| Transcend | TS128GMSA370       | 128 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WDS120G1G0B-00RC30 | 120 GB | 1       | 1     | 0     | 0.00   |
| ADATA     | SU655              | 120 GB | 1       | 1     | 0     | 0.00   |
| China     | SATA SSD           | 480 GB | 1       | 1     | 0     | 0.00   |
| Teclast   | 240GB A800         | 240 GB | 1       | 1     | 0     | 0.00   |
| SK hynix  | SC210 2.5 7MM      | 256 GB | 1       | 684   | 704   | 0.00   |
| SanDisk   | SSD P4             | 64 GB  | 1       | 14    | 14    | 0.00   |
| Toshiba   | KSG60ZSE512G SATA  | 512 GB | 2       | 97    | 100   | 0.00   |
| ADATA     | SP900NS38          | 256 GB | 1       | 942   | 1023  | 0.00   |
| Intenso   | SATA III SSD       | 240 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD8SNAT-128G-1006  | 128 GB | 1       | 0     | 0     | 0.00   |
| SPCC      | SSD                | 32 GB  | 1       | 919   | 1029  | 0.00   |
| SanDisk   | SD6SB1M256G1022I   | 256 GB | 1       | 400   | 474   | 0.00   |
| Crucial   | C300-CTFDDAC256MAG | 256 GB | 1       | 847   | 1008  | 0.00   |
| SPCC      | SSD170             | 55 GB  | 2       | 837   | 1016  | 0.00   |
| SK hynix  | HFS060G32MNM-1010U | 64 GB  | 1       | 822   | 1016  | 0.00   |
| Eluktro   | TRO-SSD7-500GB-PRO | 500 GB | 1       | 806   | 1016  | 0.00   |
| Kingston  | SA400S37           | 240 GB | 1       | 0     | 0     | 0.00   |
| Micron    | MTFDDAV256TBN-1... | 256 GB | 1       | 0     | 0     | 0.00   |
| Plextor   | PX-128M6MV         | 128 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD7UB3Q256G1001    | 256 GB | 1       | 71    | 100   | 0.00   |
| KingSpec  | MT-64              | 64 GB  | 1       | 0     | 0     | 0.00   |
| Kingmax   | SSD                | 240 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD8TN8U512G1001    | 512 GB | 1       | 0     | 0     | 0.00   |
| KingSpec  | ACSC2M064S25       | 63 GB  | 1       | 0     | 0     | 0.00   |
| Intel     | SSDSCMMW120A3L     | 120 GB | 1       | 649   | 1017  | 0.00   |
| ADATA     | AXM13S2-24GM-B     | 24 GB  | 1       | 628   | 1020  | 0.00   |
| QUMO      | SSD                | 480 GB | 1       | 625   | 1015  | 0.00   |
| SanDisk   | SSD U100           | 32 GB  | 2       | 8     | 503   | 0.00   |
| Samsung   | SSD PM830 2.5" 7mm | 512 GB | 1       | 614   | 1009  | 0.00   |
| Indilinx  | InM2246S3-128G     | 128 GB | 2       | 0     | 0     | 0.00   |
| Intel     | SSDSC2KW256G8L     | 256 GB | 1       | 0     | 0     | 0.00   |
| Intenso   | SSD Sata III       | 247 GB | 1       | 18    | 32    | 0.00   |
| SK hynix  | HFS128G39TNF-N3A0A | 128 GB | 1       | 0     | 0     | 0.00   |
| Smartbuy  | SSD                | 480 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | LAT-256M3S         | 256 GB | 1       | 1074  | 2017  | 0.00   |
| SK hynix  | HFS128G38MNB-2200A | 128 GB | 2       | 41    | 120   | 0.00   |
| Toshiba   | THNSNK256GVN8 M... | 256 GB | 2       | 49    | 100   | 0.00   |
| Corsair   | Force LS SSD       | 240 GB | 2       | 274   | 757   | 0.00   |
| ADATA     | SX900              | 256 GB | 2       | 580   | 1114  | 0.00   |
| Plextor   | PH6-CE120-L1       | 120 GB | 1       | 0     | 0     | 0.00   |
| Gost      | SSD120             | 120 GB | 1       | 0     | 0     | 0.00   |
| KingSpec  | MSH-256            | 256 GB | 1       | 0     | 0     | 0.00   |
| SMI       | B17A               | 240 GB | 1       | 0     | 0     | 0.00   |
| Transcend | TS120GMTS820S      | 120 GB | 1       | 0     | 0     | 0.00   |
| China     | T60                | 64 GB  | 2       | 0     | 0     | 0.00   |
| Reeinno   | ST960GB S7S3       | 960 GB | 1       | 0     | 0     | 0.00   |
| Kingston  | SH103S3240G-NV     | 240 GB | 1       | 377   | 1018  | 0.00   |
| PNY       | SSD2SC120GE2DA0... | 120 GB | 1       | 373   | 1018  | 0.00   |
| SPCC      | SSD170             | 64 GB  | 1       | 358   | 1016  | 0.00   |
| Mushkin   | MKNSSDCL120GB-DX   | 120 GB | 1       | 348   | 1006  | 0.00   |
| Lite-On   | CS1-SP32-11 M.2... | 32 GB  | 1       | 1     | 4     | 0.00   |
| Mushkin   | MKNSSDCL480GB-DX   | 480 GB | 1       | 347   | 1020  | 0.00   |
| SanDisk   | SDSSDXPS960G       | 960 GB | 1       | 13    | 39    | 0.00   |
| Lite-On   | LCH-128V2S-11 2... | 128 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD8SNAT-256G-1006  | 256 GB | 1       | 0     | 0     | 0.00   |
| KingFast  | SSD                | 64 GB  | 1       | 0     | 1     | 0.00   |
| Kingston  | SVP200S37A256G     | 256 GB | 1       | 311   | 1017  | 0.00   |
| FASTDISK  | FASTDISK 32G       | 32 GB  | 1       | 0     | 0     | 0.00   |
| GLOWAY    | STK120GS3-S7       | 120 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | CV1-8B512          | 512 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | CV3-8D256-11 SATA  | 256 GB | 1       | 0     | 0     | 0.00   |
| Patriot   | Torch LE           | 120 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD8SBAT-032G-1006  | 32 GB  | 3       | 0     | 0     | 0.00   |
| GLOWAY    | VAL64GM3-mSATA     | 64 GB  | 1       | 0     | 0     | 0.00   |
| Intel     | SSDSA2CW300G3      | 304 GB | 1       | 0     | 0     | 0.00   |
| GeIL      | ZENITH S3-120GB    | 120 GB | 1       | 245   | 1021  | 0.00   |
| Samsung   | MZ7PA256HMDR-010H1 | 256 GB | 1       | 236   | 1040  | 0.00   |
| Myung     | G3 Series          | 120 GB | 1       | 228   | 1015  | 0.00   |
| Goldenfir | T650-120G          | 128 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | S960 256           | 256 GB | 1       | 0     | 0     | 0.00   |
| Samsung   | SSD 860 PRO        | 1 TB   | 1       | 0     | 0     | 0.00   |
| SanDisk   | X600 M.2 2280 SATA | 128 GB | 1       | 0     | 0     | 0.00   |
| Zheino    | CHN25SATAS1 064    | 64 GB  | 1       | 0     | 0     | 0.00   |
| Crucial   | CT128MX100SSD1     | 128 GB | 1       | 3     | 16    | 0.00   |
| Patriot   | Pyro SE            | 240 GB | 1       | 180   | 1016  | 0.00   |
| Intel     | SSDSCKKF256G8H     | 256 GB | 1       | 17    | 100   | 0.00   |
| SanDisk   | SD8SN8U-256G-1006  | 256 GB | 3       | 175   | 1023  | 0.00   |
| Kingston  | SHPM2280P2H-240G   | 240 GB | 1       | 80    | 478   | 0.00   |
| China     | T120               | 120 GB | 1       | 0     | 0     | 0.00   |
| Faspeed   | H5-30G             | 32 GB  | 1       | 0     | 0     | 0.00   |
| Intel     | SSDSCKKW128G8      | 128 GB | 1       | 0     | 0     | 0.00   |
| Samsung   | MZ7LN128HAHQ-000L2 | 128 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | CF Card            | 16 GB  | 1       | 0     | 0     | 0.00   |
| Intel     | SSDMCEAW080A4 m... | 80 GB  | 1       | 162   | 1009  | 0.00   |
| Kingston  | SUV500240G         | 240 GB | 1       | 168   | 1151  | 0.00   |
| ADATA     | SU800              | 512 GB | 1       | 0     | 0     | 0.00   |
| AEGO      | SSD                | 240 GB | 1       | 0     | 0     | 0.00   |
| Colorful  | SL500              | 480 GB | 1       | 22    | 195   | 0.00   |
| Intel     | SSDSCKHF240A4L     | 240 GB | 1       | 114   | 1108  | 0.00   |
| Lite-On   | LSS-16L6G-HP       | 16 GB  | 1       | 125   | 1275  | 0.00   |
| Kingston  | SMS151S324G        | 24 GB  | 1       | 95    | 1022  | 0.00   |
| Plextor   | PX-32G5L           | 32 GB  | 1       | 0     | 0     | 0.00   |
| Intel     | SSDSC2KF512H6 SATA | 512 GB | 1       | 7     | 84    | 0.00   |
| Micron    | MTFDDAT064MAM-1J2  | 64 GB  | 1       | 85    | 1039  | 0.00   |
| PNY       | SSD2SC240G1SA75... | 240 GB | 1       | 7     | 88    | 0.00   |
| ADATA     | XM11 128GB-V3      | 128 GB | 1       | 77    | 1016  | 0.00   |
| Transcend | TS64GSSD340K       | 64 GB  | 1       | 74    | 1008  | 0.00   |
| Mushkin   | MKNSSDCR120GB-DX7  | 120 GB | 1       | 73    | 1016  | 0.00   |
| SanDisk   | SDSSDX480GG25      | 480 GB | 1       | 76    | 1090  | 0.00   |
| SandForce | 906190             | 64 GB  | 1       | 65    | 1018  | 0.00   |
| MicroData | MD300 128G         | 128 GB | 1       | 41    | 666   | 0.00   |
| Kingston  | SUV500MS120G       | 120 GB | 2       | 0     | 0     | 0.00   |
| Kingston  | SNS4151S316GD      | 16 GB  | 1       | 51    | 1022  | 0.00   |
| Samsung   | MZMPA128HMFU-000H1 | 128 GB | 2       | 69    | 1727  | 0.00   |
| Lite-On   | LMT-128M3M         | 128 GB | 1       | 44    | 1009  | 0.00   |
| Intel     | SSDSC2BB150G7      | 150 GB | 1       | 0     | 0     | 0.00   |
| KingDian  | S180               | 120 GB | 1       | 0     | 0     | 0.00   |
| Palit     | UVS                | 120 GB | 1       | 0     | 0     | 0.00   |
| Kingston  | SNS4151S316G       | 16 GB  | 1       | 39    | 1022  | 0.00   |
| ADATA     | SX300              | 64 GB  | 1       | 32    | 1020  | 0.00   |
| SanDisk   | SD9SN8W-128G-1006  | 128 GB | 4       | 17    | 998   | 0.00   |
| SanDisk   | TE22D10400GE8001   | 400 GB | 1       | 34    | 2047  | 0.00   |
| AMD       | R5S120GBSF         | 120 GB | 1       | 15    | 1016  | 0.00   |
| Samsung   | MZNLN128HAHQ-000H1 | 128 GB | 1       | 0     | 100   | 0.00   |
| Lite-On   | CV8-8E128-HP       | 128 GB | 2       | 0     | 1007  | 0.00   |
| SMI       | SSD DISK           | 506 GB | 1       | 0     | 1957  | 0.00   |
| Mushkin   | MKNSSDCR120GB-7    | 120 GB | 1       | 0     | 1023  | 0.00   |

SSD by Family
--------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

| MFG       | Family                 | Models | Samples | Days  | Err   | Rating |
|-----------|------------------------|--------|---------|-------|-------|--------|
| Toshiba   | HG2 Series             | 2      | 3       | 922   | 0     | 2.53   |
| Crucial   | RealSSD m4/C400        | 5      | 34      | 822   | 90    | 2.21   |
| Intel     | X25-E SSDs             | 1      | 1       | 795   | 0     | 2.18   |
| Crucial   | RealSSD m4/C400/P400   | 2      | 10      | 651   | 0     | 1.78   |
| Intel     | 510 Series SSDs        | 1      | 1       | 646   | 0     | 1.77   |
| Toshiba   | HG5 Series             | 1      | 2       | 471   | 0     | 1.29   |
| Verbatim  | Unknown                | 1      | 1       | 470   | 0     | 1.29   |
| Apple     | SD/SM/TS E/F/G SSDs    | 4      | 4       | 462   | 0     | 1.27   |
| OCZ       | SandForce Driven SSDs  | 33     | 207     | 588   | 46    | 1.25   |
| Foxline   | Unknown                | 1      | 1       | 443   | 0     | 1.22   |
| Phison    | Unknown                | 1      | 1       | 433   | 0     | 1.19   |
| Corsair   | SandForce Driven SSDs  | 19     | 96      | 578   | 99    | 1.19   |
| OCZ       | Indilinx Barefoot_2... | 12     | 90      | 478   | 3     | 1.16   |
| Toshiba   | HG3 Series             | 3      | 3       | 403   | 0     | 1.11   |
| Intel     | 730 and DC S35x0/36... | 7      | 16      | 430   | 1     | 1.08   |
| Mushkin   | SandForce Driven SSDs  | 8      | 8       | 479   | 508   | 1.05   |
| Kingston  | JMicron based SSDs     | 11     | 25      | 485   | 2     | 1.04   |
| KingShare | Unknown                | 1      | 1       | 358   | 0     | 0.98   |
| BHT       | Unknown                | 1      | 1       | 351   | 0     | 0.96   |
| Intel     | 320 Series SSDs        | 6      | 19      | 350   | 0     | 0.96   |
| Advantech | Unknown                | 1      | 1       | 345   | 0     | 0.95   |
| Intel     | 520 Series SSDs        | 2      | 4       | 326   | 0     | 0.89   |
| Ramaxel   | Unknown                | 1      | 2       | 295   | 0     | 0.81   |
| ADATA     | SandForce Driven SSDs  | 8      | 51      | 336   | 8     | 0.76   |
| Toshiba   | HG5d Series            | 7      | 10      | 273   | 0     | 0.75   |
| Crucial   | MX100/MX200/M5x0/M6... | 7      | 27      | 351   | 82    | 0.72   |
| Samsung   | Samsung based SSDs     | 124    | 768     | 263   | 14    | 0.70   |
| Intel     | 330/335 Series SSDs    | 2      | 10      | 252   | 0     | 0.69   |
| Crucial   | MX100/M500/M510/M55... | 1      | 6       | 252   | 0     | 0.69   |
| Crucial   | RealSSD C300/M500      | 6      | 29      | 418   | 80    | 0.69   |
| Kingston  | SandForce Driven SSDs  | 32     | 616     | 257   | 69    | 0.61   |
| Toshiba   | HG6 Series SSD         | 6      | 13      | 218   | 0     | 0.60   |
| Intel     | X18-M/X25-M/X25-V G... | 9      | 16      | 588   | 8     | 0.59   |
| Apple     | JMicron based SSDs     | 3      | 5       | 196   | 0     | 0.54   |
| OCZ       | Indilinx Barefoot 3... | 11     | 36      | 205   | 1     | 0.52   |
| Smartbuy  | Phison Driven SSDs     | 1      | 52      | 188   | 0     | 0.52   |
| Plextor   | M3/M5 (Pro) Series ... | 6      | 17      | 250   | 62    | 0.51   |
| OCZ       | Trion SSDs             | 4      | 14      | 187   | 1     | 0.49   |
| SanDisk   | Marvell based SanDi... | 33     | 113     | 198   | 42    | 0.49   |
| ADATA     | JMicron based SSDs     | 5      | 17      | 176   | 1     | 0.47   |
| Smartbuy  | Unknown                | 11     | 48      | 169   | 1     | 0.45   |
| Micron    | Unknown                | 5      | 5       | 299   | 211   | 0.45   |
| Toshiba   | Unknown                | 22     | 41      | 172   | 10    | 0.45   |
| Transcend | SandForce Driven SSDs  | 5      | 7       | 155   | 0     | 0.43   |
| Crucial   | MX1/2/300, M5/600, ... | 7      | 27      | 167   | 17    | 0.41   |
| SanDisk   | SanDisk based SSDs     | 20     | 95      | 167   | 28    | 0.41   |
| Intel     | 525 Series SSDs        | 1      | 2       | 148   | 0     | 0.41   |
| OCZ       | Indilinx Barefoot b... | 2      | 3       | 163   | 1     | 0.39   |
| Transcend | JMicron based SSDs     | 6      | 11      | 148   | 92    | 0.39   |
| SPCC      | Unknown                | 20     | 226     | 199   | 153   | 0.38   |
| Intel     | X18-M/X25-M G1 SSDs    | 2      | 2       | 139   | 0     | 0.38   |
| Intel     | Unknown                | 12     | 15      | 210   | 222   | 0.38   |
| Corsair   | Indilinx Barefoot b... | 2      | 2       | 171   | 2     | 0.37   |
| Goodram   | Unknown                | 14     | 24      | 133   | 1     | 0.36   |
| WDC       | Blue PC SSD            | 3      | 11      | 129   | 0     | 0.35   |
| Goodram   | Phison Driven SSDs     | 1      | 17      | 126   | 0     | 0.35   |
| Chiprex   | Unknown                | 1      | 1       | 126   | 0     | 0.35   |
| Intel     | 530 Series SSDs        | 4      | 37      | 147   | 1     | 0.34   |
| HP        | Unknown                | 2      | 2       | 125   | 0     | 0.34   |
| OCZ       | Unknown                | 9      | 16      | 265   | 64    | 0.34   |
| Kingston  | Unknown                | 34     | 126     | 135   | 57    | 0.33   |
| Plextor   | Unknown                | 25     | 51      | 123   | 1     | 0.31   |
| PNY       | Phison Driven SSDs     | 3      | 5       | 114   | 0     | 0.31   |
| KingDian  | SiliconMotion based... | 2      | 7       | 113   | 0     | 0.31   |
| Corsair   | Unknown                | 12     | 17      | 341   | 43    | 0.31   |
| Intel     | 730 and DC S3500/S3... | 3      | 3       | 110   | 0     | 0.30   |
| Mushkin   | SiliconMotion based... | 1      | 1       | 107   | 0     | 0.30   |
| Micron    | BX/MX1/2/3/500, M5/... | 4      | 10      | 146   | 1     | 0.29   |
| Palit     | Unknown                | 2      | 2       | 103   | 0     | 0.28   |
| Transcend | Indilinx Barefoot b... | 1      | 1       | 309   | 2     | 0.28   |
| Toshiba   | OCZ                    | 5      | 14      | 102   | 0     | 0.28   |
| Patriot   | Unknown                | 15     | 42      | 105   | 25    | 0.28   |
| Team      | Unknown                | 8      | 11      | 98    | 0     | 0.27   |
| Toshiba   | HG6 Series             | 1      | 1       | 98    | 0     | 0.27   |
| Anobit    | Unknown                | 1      | 1       | 96    | 0     | 0.27   |
| Plextor   | M3/M5/M6 Series SSDs   | 12     | 142     | 105   | 16    | 0.26   |
| KingFast  | Unknown                | 7      | 19      | 94    | 1     | 0.26   |
| SK hynix  | Unknown                | 15     | 20      | 200   | 68    | 0.26   |
| Crucial   | BX/MX1/2/3/500, M5/... | 17     | 51      | 93    | 1     | 0.25   |
| Intel     | 53x and Pro 2500 Se... | 7      | 15      | 88    | 0     | 0.24   |
| SanDisk   | Unknown                | 51     | 90      | 94    | 83    | 0.22   |
| Samsung   | Unknown                | 20     | 43      | 90    | 1     | 0.22   |
| Seagate   | 600 Series             | 1      | 1       | 79    | 0     | 0.22   |
| China     | Unknown                | 24     | 113     | 80    | 1     | 0.20   |
| Apacer    | Unknown                | 9      | 19      | 70    | 0     | 0.19   |
| Toshiba   | OCZ/Toshiba Trion SSDs | 1      | 2       | 70    | 0     | 0.19   |
| WDC       | Unknown                | 2      | 5       | 68    | 0     | 0.19   |
| Kingston  | Phison Driven SSDs     | 12     | 156     | 70    | 2     | 0.18   |
| PNY       | Unknown                | 9      | 11      | 100   | 101   | 0.18   |
| SK hynix  | SATA SSDs              | 12     | 25      | 124   | 40    | 0.17   |
| Intenso   | Unknown                | 5      | 7       | 111   | 5     | 0.17   |
| SanDisk   | SandForce Driven SSDs  | 6      | 76      | 79    | 16    | 0.17   |
| ADATA     | Unknown                | 34     | 93      | 166   | 158   | 0.17   |
| PHISON    | Unknown                | 1      | 1       | 121   | 1     | 0.17   |
| TEKET     | Unknown                | 1      | 2       | 59    | 0     | 0.16   |
| Kingmax   | Unknown                | 3      | 36      | 203   | 461   | 0.15   |
| Radeon    | Indilinx Barefoot 3... | 1      | 1       | 56    | 0     | 0.15   |
| WDC       | Green PC SSD           | 3      | 23      | 50    | 0     | 0.14   |
| Lite-On   | Unknown                | 29     | 40      | 84    | 190   | 0.13   |
| Apple     | SD/SM/TS E/F SSDs      | 4      | 4       | 48    | 0     | 0.13   |
| oyunkey   | Unknown                | 1      | 1       | 46    | 0     | 0.13   |
| Micron    | RealSSD m4/C400/P400   | 4      | 6       | 64    | 505   | 0.12   |
| PRETEC    | Unknown                | 1      | 1       | 44    | 0     | 0.12   |
| QUMO      | Unknown                | 3      | 4       | 344   | 508   | 0.12   |
| Micron    | MX1/2/300, M5/600, ... | 2      | 8       | 46    | 212   | 0.12   |
| Fordisk   | Unknown                | 2      | 2       | 41    | 0     | 0.11   |
| KingSpec  | Unknown                | 28     | 46      | 43    | 18    | 0.11   |
| Goldkey   | Unknown                | 2      | 2       | 39    | 0     | 0.11   |
| Transcend | SiliconMotion based... | 19     | 60      | 36    | 0     | 0.10   |
| OCZ       | Intrepid 3000 SSDs     | 2      | 2       | 35    | 0     | 0.10   |
| ZOTAC     | Unknown                | 1      | 2       | 34    | 0     | 0.09   |
| AMD       | SiliconMotion based... | 1      | 19      | 34    | 0     | 0.09   |
| WDC       | Blue and Green SSDs    | 10     | 50      | 35    | 1     | 0.09   |
| Toshiba   | SG2 Series             | 1      | 1       | 32    | 0     | 0.09   |
| Crucial   | SiliconMotion based... | 3      | 9       | 31    | 0     | 0.09   |
| KingDian  | Unknown                | 11     | 40      | 31    | 29    | 0.08   |
| KingPower | Unknown                | 1      | 1       | 29    | 0     | 0.08   |
| AMD       | Unknown                | 7      | 19      | 42    | 54    | 0.08   |
| Faspeed   | Unknown                | 4      | 4       | 27    | 0     | 0.08   |
| SenDisk   | Unknown                | 1      | 1       | 27    | 0     | 0.08   |
| Intel     | 545s Series SSDs       | 5      | 14      | 25    | 0     | 0.07   |
| e2e4      | Unknown                | 1      | 2       | 22    | 0     | 0.06   |
| Mushkin   | Unknown                | 2      | 3       | 94    | 339   | 0.06   |
| XUNZHE    | Unknown                | 1      | 1       | 20    | 0     | 0.05   |
| Netac     | Unknown                | 1      | 1       | 19    | 0     | 0.05   |
| Zheino    | Unknown                | 4      | 6       | 19    | 0     | 0.05   |
| Kingrich  | Unknown                | 2      | 3       | 19    | 0     | 0.05   |
| Hyperdisk | Unknown                | 1      | 1       | 18    | 0     | 0.05   |
| ADATA     | SiliconMotion based... | 2      | 24      | 18    | 1     | 0.05   |
| Londisk   | Unknown                | 3      | 5       | 17    | 0     | 0.05   |
| LDLC      | Unknown                | 2      | 5       | 16    | 0     | 0.05   |
| LDNDISK   | Unknown                | 1      | 1       | 16    | 0     | 0.05   |
| Platinet  | Unknown                | 1      | 1       | 16    | 0     | 0.04   |
| Seagate   | 600 Pro Series         | 1      | 1       | 14    | 0     | 0.04   |
| Apple     | MacBook Air SSD        | 1      | 1       | 128   | 8     | 0.04   |
| Micron    | MX100/MX200/M5x0/M6... | 1      | 1       | 13    | 0     | 0.04   |
| Transcend | Unknown                | 6      | 13      | 13    | 0     | 0.04   |
| TCSUNBOW  | Unknown                | 1      | 1       | 13    | 0     | 0.04   |
| Crucial   | Unknown                | 1      | 1       | 11    | 0     | 0.03   |
| Lenovo    | Unknown                | 2      | 2       | 11    | 0     | 0.03   |
| GLOWAY    | Unknown                | 4      | 5       | 11    | 0     | 0.03   |
| GeIL      | Unknown                | 6      | 7       | 45    | 146   | 0.03   |
| Seagate   | Unknown                | 2      | 2       | 10    | 0     | 0.03   |
| FORESEE   | Unknown                | 3      | 5       | 9     | 0     | 0.03   |
| Intel     | 540 Series SSDs        | 2      | 5       | 17    | 3     | 0.02   |
| BIWIN     | Unknown                | 3      | 4       | 7     | 0     | 0.02   |
| FASTDISK  | Unknown                | 6      | 6       | 7     | 0     | 0.02   |
| Integral  | Unknown                | 1      | 1       | 6     | 0     | 0.02   |
| Vaseky    | Unknown                | 1      | 1       | 5     | 0     | 0.01   |
| Drevo     | Unknown                | 1      | 2       | 314   | 34    | 0.01   |
| Teclast   | Unknown                | 2      | 2       | 4     | 0     | 0.01   |
| Dell      | Unknown                | 3      | 3       | 3     | 0     | 0.01   |
| ShineDisk | Unknown                | 1      | 1       | 3     | 0     | 0.01   |
| i-Flas... | Unknown                | 1      | 1       | 3     | 0     | 0.01   |
| Apacer    | SDM5/5A/5A-M Series... | 1      | 1       | 33    | 10    | 0.01   |
| Kingch... | Unknown                | 1      | 1       | 2     | 0     | 0.01   |
| MicroData | Unknown                | 2      | 2       | 23    | 333   | 0.01   |
| Gigastone | Unknown                | 1      | 1       | 2     | 0     | 0.01   |
| Gigabyte  | Unknown                | 2      | 3       | 2     | 0     | 0.01   |
| ACPI      | Unknown                | 1      | 1       | 2     | 0     | 0.01   |
| Golden... | Unknown                | 1      | 1       | 1     | 0     | 0.01   |
| Crucial   | RealSSD C300/P300      | 1      | 1       | 847   | 1008  | 0.00   |
| Eluktro   | Unknown                | 1      | 1       | 806   | 1016  | 0.00   |
| Indilinx  | Unknown                | 1      | 2       | 0     | 0     | 0.00   |
| Gost      | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| Reeinno   | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| Myung     | Unknown                | 1      | 1       | 228   | 1015  | 0.00   |
| SMI       | Unknown                | 2      | 2       | 0     | 979   | 0.00   |
| Goldenfir | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| AEGO      | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| Colorful  | Unknown                | 1      | 1       | 22    | 195   | 0.00   |
| SandForce | Unknown                | 1      | 1       | 65    | 1018  | 0.00   |

SSD by Vendor
-------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

| MFG         | Models | Samples | Days  | Err   | Rating |
|-------------|--------|---------|-------|-------|--------|
| Verbatim    | 1      | 1       | 470   | 0     | 1.29   |
| Foxline     | 1      | 1       | 443   | 0     | 1.22   |
| Phison      | 1      | 1       | 433   | 0     | 1.19   |
| OCZ         | 73     | 368     | 488   | 30    | 1.07   |
| Corsair     | 33     | 115     | 536   | 89    | 1.04   |
| KingShare   | 1      | 1       | 358   | 0     | 0.98   |
| BHT         | 1      | 1       | 351   | 0     | 0.96   |
| Advantech   | 1      | 1       | 345   | 0     | 0.95   |
| Crucial     | 50     | 195     | 348   | 47    | 0.83   |
| Ramaxel     | 1      | 2       | 295   | 0     | 0.81   |
| Mushkin     | 11     | 12      | 352   | 424   | 0.74   |
| Samsung     | 144    | 811     | 254   | 14    | 0.67   |
| Apple       | 12     | 14      | 225   | 1     | 0.60   |
| Toshiba     | 49     | 90      | 214   | 5     | 0.58   |
| Intel       | 64     | 160     | 247   | 22    | 0.53   |
| Kingston    | 89     | 923     | 215   | 54    | 0.51   |
| Smartbuy    | 12     | 100     | 179   | 1     | 0.49   |
| SPCC        | 20     | 226     | 199   | 153   | 0.38   |
| Goodram     | 15     | 41      | 130   | 1     | 0.36   |
| Chiprex     | 1      | 1       | 126   | 0     | 0.35   |
| HP          | 2      | 2       | 125   | 0     | 0.34   |
| ADATA       | 49     | 185     | 195   | 82    | 0.34   |
| SanDisk     | 110    | 374     | 141   | 43    | 0.34   |
| Plextor     | 43     | 210     | 121   | 16    | 0.29   |
| Palit       | 2      | 2       | 103   | 0     | 0.28   |
| Patriot     | 15     | 42      | 105   | 25    | 0.28   |
| Team        | 8      | 11      | 98    | 0     | 0.27   |
| Anobit      | 1      | 1       | 96    | 0     | 0.27   |
| KingFast    | 7      | 19      | 94    | 1     | 0.26   |
| Micron      | 16     | 30      | 124   | 193   | 0.23   |
| PNY         | 12     | 16      | 104   | 70    | 0.22   |
| SK hynix    | 27     | 45      | 158   | 52    | 0.21   |
| China       | 24     | 113     | 80    | 1     | 0.20   |
| Apacer      | 10     | 20      | 68    | 1     | 0.18   |
| Intenso     | 5      | 7       | 111   | 5     | 0.17   |
| PHISON      | 1      | 1       | 121   | 1     | 0.17   |
| TEKET       | 1      | 2       | 59    | 0     | 0.16   |
| Kingmax     | 3      | 36      | 203   | 461   | 0.15   |
| Radeon      | 1      | 1       | 56    | 0     | 0.15   |
| Transcend   | 37     | 92      | 58    | 11    | 0.15   |
| WDC         | 18     | 89      | 52    | 1     | 0.14   |
| Lite-On     | 29     | 40      | 84    | 190   | 0.13   |
| oyunkey     | 1      | 1       | 46    | 0     | 0.13   |
| PRETEC      | 1      | 1       | 44    | 0     | 0.12   |
| QUMO        | 3      | 4       | 344   | 508   | 0.12   |
| KingDian    | 13     | 47      | 43    | 25    | 0.12   |
| Fordisk     | 2      | 2       | 41    | 0     | 0.11   |
| KingSpec    | 28     | 46      | 43    | 18    | 0.11   |
| Goldkey     | 2      | 2       | 39    | 0     | 0.11   |
| ZOTAC       | 1      | 2       | 34    | 0     | 0.09   |
| AMD         | 8      | 38      | 38    | 27    | 0.09   |
| KingPower   | 1      | 1       | 29    | 0     | 0.08   |
| Seagate     | 4      | 4       | 28    | 0     | 0.08   |
| Faspeed     | 4      | 4       | 27    | 0     | 0.08   |
| SenDisk     | 1      | 1       | 27    | 0     | 0.08   |
| e2e4        | 1      | 2       | 22    | 0     | 0.06   |
| XUNZHE      | 1      | 1       | 20    | 0     | 0.05   |
| Netac       | 1      | 1       | 19    | 0     | 0.05   |
| Zheino      | 4      | 6       | 19    | 0     | 0.05   |
| Kingrich    | 2      | 3       | 19    | 0     | 0.05   |
| Hyperdisk   | 1      | 1       | 18    | 0     | 0.05   |
| Londisk     | 3      | 5       | 17    | 0     | 0.05   |
| LDLC        | 2      | 5       | 16    | 0     | 0.05   |
| LDNDISK     | 1      | 1       | 16    | 0     | 0.05   |
| Platinet    | 1      | 1       | 16    | 0     | 0.04   |
| TCSUNBOW    | 1      | 1       | 13    | 0     | 0.04   |
| Lenovo      | 2      | 2       | 11    | 0     | 0.03   |
| GLOWAY      | 4      | 5       | 11    | 0     | 0.03   |
| GeIL        | 6      | 7       | 45    | 146   | 0.03   |
| FORESEE     | 3      | 5       | 9     | 0     | 0.03   |
| BIWIN       | 3      | 4       | 7     | 0     | 0.02   |
| FASTDISK    | 6      | 6       | 7     | 0     | 0.02   |
| Integral    | 1      | 1       | 6     | 0     | 0.02   |
| Vaseky      | 1      | 1       | 5     | 0     | 0.01   |
| Drevo       | 1      | 2       | 314   | 34    | 0.01   |
| Teclast     | 2      | 2       | 4     | 0     | 0.01   |
| Dell        | 3      | 3       | 3     | 0     | 0.01   |
| ShineDisk   | 1      | 1       | 3     | 0     | 0.01   |
| i-FlashDisk | 1      | 1       | 3     | 0     | 0.01   |
| Kingchuxing | 1      | 1       | 2     | 0     | 0.01   |
| MicroData   | 2      | 2       | 23    | 333   | 0.01   |
| Gigastone   | 1      | 1       | 2     | 0     | 0.01   |
| Gigabyte    | 2      | 3       | 2     | 0     | 0.01   |
| ACPI        | 1      | 1       | 2     | 0     | 0.01   |
| Goldendisk  | 1      | 1       | 1     | 0     | 0.01   |
| Eluktro     | 1      | 1       | 806   | 1016  | 0.00   |
| Indilinx    | 1      | 2       | 0     | 0     | 0.00   |
| Gost        | 1      | 1       | 0     | 0     | 0.00   |
| Reeinno     | 1      | 1       | 0     | 0     | 0.00   |
| Myung       | 1      | 1       | 228   | 1015  | 0.00   |
| SMI         | 2      | 2       | 0     | 979   | 0.00   |
| Goldenfir   | 1      | 1       | 0     | 0     | 0.00   |
| AEGO        | 1      | 1       | 0     | 0     | 0.00   |
| Colorful    | 1      | 1       | 22    | 195   | 0.00   |
| SandForce   | 1      | 1       | 65    | 1018  | 0.00   |

