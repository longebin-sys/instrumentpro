InstrumentPro Responsive Master Update

This version adds STYLE-20: UNIVERSAL RESPONSIVE / DEVICE ADAPTIVE LAYOUT.

The existing application logic and page structure are preserved. The update:
- removes the global 480px body restriction
- makes the app shell fluid from small phones through large desktop screens
- keeps content readable with a desktop max-width
- makes bottom navigation adapt to viewport width
- adds safe-area support for iPhone/notched and gesture-navigation devices
- handles narrow phones, tablets, desktops, and landscape windows
- prevents common horizontal overflow from long labels, inputs and media
- preserves the existing mobile layout behavior where possible

Replace the repository's existing index.html with the included index.html.
