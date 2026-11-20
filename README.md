# New, unnamed Constellation Atlas project receiving folder

This is **not Seasify**. Do not assign a brand until instructed. Create its separate Git repository only after explicit remote/visibility confirmation. No original UI reference has been supplied in this package yet.

Read `../04_Implementation/PROJECTS/CONSTELLATION_IMPLEMENTATION.md` and `../04_Implementation/DESIGN_CONSTITUTION.md`.

## Sky data and verification

- Use the [IAU constellation list](https://www.iau.org/IAU/Astronomy-FAQs/Constellations.aspx) for the 88 canonical names and abbreviations. Keep the catalog of constellation figures separate so line art can carry its own cultural attribution.
- Evaluate [CDS VizieR VI/49](https://cdsarc.cds.unistra.fr/viz-bin/ReadMe/VI/49?format=html&tex=true) for boundary geometry. Record the source table, coordinate frame, epoch, and redistribution terms before bundling it. If using the B1875 table, sample along its boundary segments before converting them to the renderer's frame. Use [VI/42](https://cdsarc.cds.unistra.fr/viz-bin/cat/VI/42) for an independent position-to-constellation check.
- Evaluate [Astronomy Engine's JavaScript browser API](https://github.com/cosinekitty/astronomy/blob/master/demo/browser/README.md) for altitude and azimuth from an observer and UTC instant. Select and document the refraction mode. Validate the coordinate conversion at both hemispheres, the RA wrap, and the horizon using independent reference positions.
