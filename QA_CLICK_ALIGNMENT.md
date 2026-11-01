# Home Equity Studio V4.1.3 — Footer link alignment hotfix

## Cause
The desktop landing page is a fixed approved-artwork image with transparent clickable hotspot links. In the prior build, the phone/CEA hotspot coordinates were about 5 percentage points too high on the vertical axis.

## Fix
- Mobile contact number: positioned at `left:17.9%; top:94.5%; width:7.1%; height:2.6%` of the artwork.
- Verify with CEA: positioned at `left:25.45%; top:94.5%; width:7.8%; height:2.6%` of the artwork.
- Destinations: `tel:+6589809229` and official CEA registration verification URL.
- Existing design, profile portrait, other page HTML and calculation formulas retained.

## Browser checks
Using in-memory Chromium DOM hit tests directly at the painted text positions, click destinations passed at desktop widths 1448px, 1280px and 1101px. Mobile text links confirmed at 1024px, 768px, 390px and 320px. No horizontal overflow or JavaScript errors at any checked width.

These tests verify local browser hit regions and destinations. Live Vercel deployment / native iPhone Safari were not tested.
