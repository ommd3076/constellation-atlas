# Astronomical Coordinate & Ephemeris Standards

## 1. Celestial Coordinate Systems
- Equatorial Coordinates: Right Ascension (RA: hours, minutes, seconds or decimal degrees [0, 360)) and Declination (Dec: degrees [-90, +90]).
- Reference Epoch: Standard J2000.0 (JD 2451545.0) for fixed-star catalog references.
- Precession & Proper Motion: Ephemeris transformations follow IAU 2006 precession formulas for epoch adjustments.

## 2. Observer-Relative Frame
- Horizontal Coordinates: Altitude (Alt: [-90, +90]) and Azimuth (Az: [0, 360) measured North through East).
- Local Sidereal Time (LST) computed from UTC instant and observer longitude.
- Atmospheric Refraction: Bennett's empirical refraction formula applied for Alt > -1 deg; unrefracted geometric mode available for scientific comparison.

## 3. Boundary Sampling & Polygon Representation
- Source Catalog: CDS VizieR VI/49 (Delporte 1930 boundary arcs).
- Boundary segments are sampled along constant RA arcs (meridians) and constant Dec arcs (parallels) with <= 0.5 deg resolution prior to spherical projection.
- Point-in-polygon classification utilizes spherical ray-casting against Delporte boundary vertices.
