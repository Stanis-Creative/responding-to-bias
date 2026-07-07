# PDF documents for inventory

**Important:** This folder is for PDF files only. Do **not** create Unity inventory item assets here — Unity will fail to open them. Create document item assets under `Assets/Inventory/Documents/` instead.

PDFs in this folder ship with Standalone builds. Each file name must match the **Pdf File Name** on a document inventory item asset.

## Add a new document

1. Copy the PDF into this folder (`Assets/StreamingAssets/Documents/`).
2. In Unity, create **Create → Inventory → Document Item** under `Assets/Inventory/Documents/` (not here).
3. On the asset, set:
   - **Item Id** — unique id (e.g. `patient_rights_handout`)
   - **Display Name** — label shown in the inventory grid
   - **Icon** — thumbnail sprite for world and inventory
   - **Pdf File Name** — file name only (e.g. `patient_rights.pdf`), not a full path
4. Place a world pickup:
   - GameObject with `SpriteRenderer`, `Collider2D`, and `WorldPickupItem`
   - Assign the document item asset and the scene’s `InventoryRunner`
5. Test in Play mode: click the object to pick up, open the backpack, click the slot to open the PDF in the system viewer.

## Notes

- Pickups hide after collection and stay hidden when returning to a scene if the item is already in session.
- Opening PDFs uses the system viewer on desktop (macOS/Windows) and opens a new browser tab on WebGL. Platform code lives in `Assets/Scripts/Platform/`.
- Bias card items are unchanged; only **Document Item** assets open a PDF when clicked in the inventory.
