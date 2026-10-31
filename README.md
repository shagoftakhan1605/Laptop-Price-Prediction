# Laptop Price Prediction

Predicts laptop prices from their specifications with a Random Forest regressor, and provides an interactive form built with ipywidgets (it can also be served as a web app with Voilà).

All code is in [`Laptop_Data_Project_Web.ipynb`](Laptop_Data_Project_Web.ipynb). The dataset is `laptopData.csv` and `image.jpg` is the picture shown in the form.

---

## Dataset

* `laptopData.csv`: 1,303 laptops with company, type, screen size and resolution, CPU, RAM, storage, GPU, operating system, weight and price
* After cleaning, 1,254 laptops are used
* Prices are as given in the dataset (currency not stated in the file)
* Original source: *to be added*

## Features Used

Company, laptop type, screen size, RAM, GPU brand, operating system (Windows, Mac or other), weight, screen resolution, touchscreen, CPU frequency, CPU brand, storage size, storage type and second storage type. Text fields are parsed into numbers or categories (for example `8GB` to 8, `Intel Core i5 2.3GHz` to brand and frequency) and categories are encoded as integer codes.

---

## Model and Results

* Random Forest regressor (scikit-learn defaults, `random_state=42`)
* Random 80/20 train and test split
* **Test R²: 0.84**, **test MAE: about 10,000** (the median test price is about 56,500)

R² stays between 0.83 and 0.85 for different random seeds.

---

## How to Run

```bash
pip install -r requirements.txt
jupyter notebook Laptop_Data_Project_Web.ipynb
```

Run all cells, choose the laptop specifications in the form and click **Predict the Price**.

To open it as a stand-alone web page:

```bash
voila Laptop_Data_Project_Web.ipynb
```

---

## Changes in This Version

* Data are now read from `laptopData.csv` in the repository instead of a fixed Windows path
* Test R² and MAE are computed in the notebook (this code was commented out before)
* Removed leftover cells that exported package lists and read a file not in the repository
* `requirements.txt` reduced to the packages the notebook actually uses

---

## Limitations

* Categories are encoded as integer codes, which imposes an artificial order; one-hot encoding may work better for some models
* Only one train and test split; cross-validation would give a more reliable estimate
* Prices are not adjusted for the year of release

---

## Tools

Python, pandas, NumPy, scikit-learn, ipywidgets, Voilà
