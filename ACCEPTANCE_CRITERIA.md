# Gear-Based Progress Bar - Acceptance Criteria

## AC-1: Gear Generation & Specification
**Requirement:** FR-1, FR-2

**Acceptance Criteria:**
- [ ] Gears can be generated with tooth counts from 3 to MAX_GEAR_TEETH
- [ ] Each gear's size is calculated correctly from its tooth count using standard involute gear mathematics
- [ ] A gear can be placed at any random position within the rectangle
- [ ] The system can sequentially place multiple gears

## AC-2: First Gear Placement
**Requirement:** FR-2

**Acceptance Criteria:**
- [ ] When initialization begins, the first gear is placed at a random position within the rectangle
- [ ] The first gear's position is completely within rectangle bounds
- [ ] The first gear is used as the reference point for subsequent placements

## AC-3: Gear Connectivity (No Floating Gears)
**Requirement:** FR-2, C-1

**Acceptance Criteria:**
- [ ] Every gear placed after the first must mesh with at least one existing gear
- [ ] No gear exists that does not mesh with any other gear
- [ ] Attempting to place a gear that would not mesh with any existing gear fails and is rejected
- [ ] At least 2 gears are placed (or test with single gear scenario)

## AC-4: Single Mesh System (No Islands)
**Requirement:** FR-2, C-1

**Acceptance Criteria:**
- [ ] All placed gears form a single connected mesh system
- [ ] No subset of gears is isolated from the rest (no islands)
- [ ] A graph traversal from any gear can reach every other gear through meshing relationships

## AC-5: Rectangle Boundary Compliance
**Requirement:** FR-6, C-2

**Acceptance Criteria:**
- [ ] Every gear is fully contained within the rectangle
- [ ] No gear extends beyond the rectangle boundaries
- [ ] When a gear placement would cause any part to exceed bounds, placement is rejected
- [ ] Gears positioned near edges do not clip through boundaries

## AC-6: Space Filling
**Requirement:** FR-2

**Acceptance Criteria:**
- [ ] The algorithm attempts to place gears until no more can fit
- [ ] The final configuration has the maximum number of gears that can fit in the rectangle given the current parameters
- [ ] When a placement iteration fails (no valid gear can be placed), the algorithm terminates

## AC-7: Meshing Validation
**Requirement:** FR-3, C-4

**Acceptance Criteria:**
- [ ] Two gears are considered meshed if their teeth touch without overlapping
- [ ] Meshing is determined using standard involute gear mathematics
- [ ] Teeth of meshing gears do not overlap
- [ ] Gears that do not mesh do not touch

## AC-8: Gear Ratio Calculation
**Requirement:** FR-3, FR-5

**Acceptance Criteria:**
- [ ] The gear ratio between two meshing gears is correctly calculated as tooth_count_1 / tooth_count_2
- [ ] The system correctly identifies which gears are meshed together
- [ ] Gear ratios propagate through the system (gear A meshes B, B meshes C → ratios are transitive)

## AC-9: Rotation Synchronization
**Requirement:** FR-5

**Acceptance Criteria:**
- [ ] All gears rotate at speeds determined by their gear ratios relative to the first gear
- [ ] Rotating the first gear at speed S causes a meshed gear with ratio R to rotate at speed S/R
- [ ] The rotation system is internally consistent (no contradictions in gear speeds)
- [ ] Adjacent meshing gears rotate in the correct direction relative to each other

## AC-10: Progress Bar Control
**Requirement:** FR-5, UI-2

**Acceptance Criteria:**
- [ ] Progress slider accepts values from 0 to 100
- [ ] Moving the slider updates gear rotation immediately
- [ ] Progress value 0 shows gears at initial rotation
- [ ] Progress value 100 shows maximum rotation (full or partial rotation is acceptable)
- [ ] Intermediate progress values produce proportional rotation

## AC-11: Radius Range Controls
**Requirement:** FR-2, UI-4

**Acceptance Criteria:**
- [ ] Minimum radius slider limits the smallest gear that can be generated
- [ ] Maximum radius slider limits the largest gear that can be generated
- [ ] Only gears with radius between min and max are considered for placement
- [ ] Adjusting sliders allows re-generation of gear configurations with different size ranges
- [ ] Min radius slider value is less than or equal to max radius slider value

## AC-12: Tooth Parameter Controls
**Requirement:** FR-7, UI-5, UI-6

**Acceptance Criteria:**
- [ ] Tooth depth parameter can be adjusted and affects gear tooth visual height
- [ ] Tooth width parameter can be adjusted and affects gear tooth visual width
- [ ] Tooth roundness parameter can be adjusted and affects tooth profile curvature
- [ ] Hole radius parameter can be adjusted and affects gear center hole size
- [ ] All parameters follow standard involute gear mathematics conventions
- [ ] Changing parameters allows re-generation of gears with new characteristics

## AC-13: Tooth Shape Selection
**Requirement:** UI-3

**Acceptance Criteria:**
- [ ] Two tooth shape options are available: "Square" and "Sharp"
- [ ] Selection is mutually exclusive (only one shape selected at a time)
- [ ] Changing tooth shape visually updates gear appearance
- [ ] Tooth shape affects gear rendering but not meshing math

## AC-14: Color Control
**Requirement:** UI-3

**Acceptance Criteria:**
- [ ] A color picker (button: "Change Color") allows selection of gear color
- [ ] Selected color is applied to all gears
- [ ] Color change is immediately visible
- [ ] Color persists across parameter changes and rotation

## AC-15: Full UI Integration
**Requirement:** UI-1, UI-2, UI-3, UI-4, UI-5, UI-6

**Acceptance Criteria:**
- [ ] All UI controls are functional and responsive
- [ ] Gear visualization updates when any parameter changes
- [ ] Progress slider and gear rotation are synchronized
- [ ] UI layout matches the provided design mockup
- [ ] All sliders and controls are accessible and usable

## AC-16: Edge Cases
**Requirement:** FR-2, C-1, C-3

**Acceptance Criteria:**
- [ ] System handles single gear scenario (first gear with no additional gears that can mesh)
- [ ] System handles tooth count boundaries (3-tooth and MAX_TOOTH gears)
- [ ] System handles full rectangle scenario (no room for additional gears)
- [ ] System handles minimum radius scenario (no valid gears between min and max)

## AC-17: Placement Algorithm
**Requirement:** FR-4

**Acceptance Criteria:**
- [ ] The algorithm identifies valid arcs where new gears can mesh with existing gears
- [ ] Random point selection on valid arcs produces varied but valid placements
- [ ] Algorithm avoids creating floating gears or islands
- [ ] Algorithm adapts gear selection metrics when placement fails with one approach
- [ ] Algorithm terminates when no more gears can be placed

## AC-18: Visual Representation
**Requirement:** FR-1, UI-1

**Acceptance Criteria:**
- [ ] Gears are rendered with visible teeth
- [ ] Gear positions and sizes reflect their mathematical properties
- [ ] Gear rotation is visually apparent
- [ ] Teeth engagement is visually apparent for meshing gears
- [ ] Empty space in rectangle is visually distinguishable from filled space
