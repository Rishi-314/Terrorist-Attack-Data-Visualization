# Terrorist-Attack-Data-Visualization

from pathlib import Path

root = Path(r"c:\Users\RISHIKESH\OneDrive\Desktop\VGPay-SoundBox\Terrorist-Attack-Data-Visualization")
images_dir = root / "images"
images_dir.mkdir(exist_ok=True)

svg_path = images_dir / "terrorism_overview.svg"
svg_path.write_text(
    """<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="600" viewBox="0 0 1200 600">
  <rect width="1200" height="600" fill="#0f172a"/>
  <rect x="60" y="60" width="1080" height="480" rx="24" fill="#111827" stroke="#334155" stroke-width="2"/>
  <text x="600" y="180" text-anchor="middle" font-family="Segoe UI, Arial, sans-serif" font-size="40" font-weight="700" fill="#f8fafc">
    Terrorist Attack Data Visualization
  </text>
  <text x="600" y="235" text-anchor="middle" font-family="Segoe UI, Arial, sans-serif" font-size="22" fill="#cbd5e1">
    Analysis of the Global Terrorism Database (GTD)
  </text>

  <path d="M180 360 C250 300, 320 290, 390 320
           C450 345, 500 360, 560 340
           C620 320, 690 270, 760 285
           C820 298, 870 340, 930 345
           C980 350, 1020 330, 1060 300"
        fill="none" stroke="#38bdf8" stroke-width="4" stroke-opacity="0.7"/>

  <circle cx="240" cy="320" r="8" fill="#f43f5e"/>
  <circle cx="390" cy="320" r="8" fill="#f43f5e"/>
  <circle cx="560" cy="340" r="8" fill="#f43f5e"/>
  <circle cx="760" cy="285" r="8" fill="#f43f5e"/>
  <circle cx="930" cy="345" r="8" fill="#f43f5e"/>

  <rect x="210" y="395" width="220" height="80" rx="12" fill="#1e293b"/>
  <text x="320" y="430" text-anchor="middle" font-family="Segoe UI, Arial, sans-serif" font-size="20" font-weight="600" fill="#f8fafc">
    EDA & Statistics
  </text>

  <rect x="490" y="395" width="220" height="80" rx="12" fill="#1e293b"/>
  <text x="600" y="430" text-anchor="middle" font-family="Segoe UI, Arial, sans-serif" font-size="20" font-weight="600" fill="#f8fafc">
    Maps & Charts
  </text>

  <rect x="770" y="395" width="220" height="80" rx="12" fill="#1e293b"/>
  <text x="880" y="430" text-anchor="middle" font-family="Segoe UI, Arial, sans-serif" font-size="20" font-weight="600" fill="#f8fafc">
    Clustering & ML
  </text>
</svg>""",
    encoding="utf-8"
)

readme_path = root / "README.md"
readme_path.write_text(
    """# Terrorist-Attack-Data-Visualization

![Terrorist Attack Data Visualization](images/terrorism_overview.svg)

This project explores the Global Terrorism Database (GTD) using Python and Jupyter Notebook to analyze and visualize terrorist attacks worldwide.

## Dataset

- Source: [Global Terrorism Database (GTD)](https://www.kaggle.com/datasets/START-UMD/gtd)
- Description: A comprehensive dataset containing information about terrorist incidents, including date, location, attack type, target type, weapon type, casualties, and outcome.

## Project Overview

This notebook includes:
- Data cleaning and preprocessing
- Exploratory data analysis (EDA)
- Statistical analysis
- Visualizations using Matplotlib and Seaborn
- Interactive maps using Plotly and Folium
- Dimensionality reduction and clustering with scikit-learn

## Files

- `Visualization.ipynb` - Main notebook with the full analysis and visualizations

## Requirements

Install the required Python libraries:

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn networkx plotly folium jupyter
```
""",
    encoding="utf-8"
)

images_svg = root / "images" / "terrorism_overview.svg"
if not images_svg.exists():
   images_svg = None
# check dataset cover
dataset_cover_candidates = [root/"dataset-cover.png", root/"images"/"dataset-cover.png"]
dataset_cover_path = next((p for p in dataset_cover_candidates if p.exists()), None)
# build image markdown lines
image_lines = []
if images_svg is not None:
   image_lines.append(f"![Terrorist Attack Data Visualization]({images_svg.relative_to(root).as_posix()})")
if dataset_cover_path is not None:
   image_lines.append(f"![Dataset Cover]({dataset_cover_path.relative_to(root).as_posix()})")
else:
   image_lines.append("![Dataset Cover](dataset-cover.png)")
content = f"""# Terrorist-Attack-Data-Visualization

{...}
"""
readme_path.write_text(content, encoding="utf-8")