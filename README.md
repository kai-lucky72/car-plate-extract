# Car Number Plate Extraction (3-Step Pipeline)

This project implements a classical, CPU-only plate extraction pipeline:

1. Plate detection (contours + geometry)
2. Plate alignment (perspective transform)
3. OCR + regex validation + temporal confirmation

## Folder Structure

- `data/plates/` - optional plate snapshots (not used by default)
- `data/logs/` - CSV logs
- `src/` - runnable stages
- `book/` - placeholder for the PDF

## Setup

The virtual environment and packages are already available. If you need to reinstall:

```powershell
python -m pip install --upgrade pip setuptools wheel
python -m pip install -r requirements.txt
```

Tesseract OCR must be installed on your system and available on `PATH`.

## Run Each Stage

Camera test:

```powershell
python src\camera.py
```

Plate detection:

```powershell
python src\detect.py
```

Plate alignment:

```powershell
python src\align.py
```

OCR test:

```powershell
python src\ocr.py
```

Regex validation:

```powershell
python src\validate.py
```

Temporal validation + CSV logging:

```powershell
python src\temporal.py
```

## Output

Confirmed plates are logged to:

- `data/logs/plates_log.csv`

Each entry includes the plate number and a timestamp.

## Notes

- Press `q` to quit any window.
- If your camera is not at index 0, change `cv2.VideoCapture(0)` in each file.
- If OCR returns nothing, improve lighting and ensure the plate is sharp and centered.
