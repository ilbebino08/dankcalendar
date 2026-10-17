# Scroll wheel fix

`scroll-wheel.patch` preserves the local fix and nine regression tests for
`dank-qml-common` revision `971aa3d326cb01e174d34f4dc843719386c6464f`.
It prevents wheel events with pixel deltas from starting trackpad momentum in
`DankFlickable`, `DankListView`, and `DankGridView`.

The application's pinned revision `9314fc4df5a90c95bddcda83d696a1fd8c895aea`
already implements this distinction through `DCommon/Common/WheelInput.js`.
That compatible revision was used for the tested executable. This patch is
preserved for the older `DankCommon` layout; it is not applied during builds.

Apply it inside that submodule checkout with
`git apply --unidiff-zero /path/to/patches/scroll-wheel.patch`.
