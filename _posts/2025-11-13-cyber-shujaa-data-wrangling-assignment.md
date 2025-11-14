---
title: Cyber Shujaa Data Wrangling Assignment
categories: [Data Wrangling, Cyber Shujaa]
tags: [cyber shujaa, data wrangling, python, pandas, data science, data analysis]
---

## **From Blueprints to Clean Data: Building the Foundation with Data Wrangling ✨📊**

My journey from architecture to AI is driven by a focus on **structural integrity** 
and **precision**. In architecture, a flawed foundation dooms a project. In data 
science, dirty, inconsistent data leads to unreliable, biased models.

The second assignment in the **CyberShujaa Data and AI Specialist** track was all 
about building that robust foundation. Centered on **data wrangling** with the `Netflix Dataset` 
from [Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows), the goal was 
to apply structural logic to messy, real-world data and transform it into a reliable 
asset ready for deep analysis.

This project reinforced that my core skills — attention to detail, logical sequencing, 
and rigorous validation — are perfectly transferable to constructing intelligent 
systems.

----

### **The Mission: Enforcing Data Consistency 🎯**

The purpose of this assignment was to gain hands-on experience using `Python` and 
`Pandas` to clean and validate a real-world dataset. This involved moving systematically 
through every step of the data lifecycle:

1. **Data Discovery:** Identifying data types, missing values, and formatting 
inconsistencies.
2. **Cleaning & Refining:** Handling duplicates, nulls, and correcting data types.
3. **Transformation & Enrichment:** Using filtering, grouping, and feature extraction 
(like date conversion) to prepare the data.
4. **Validation & Export:** Checking the consistency and logical accuracy of the final, 
cleaned dataset.

This systematic approach mirrors the rigorous stages of design and quality control 
in an architectural project.

For the full technical breakdown and `.ipynb` notebook, you can view my 
[Github repository](https://github.com/nadupoy/Cyber-Shujaa---Data-Wrangling) and 
my initial [Kaggle](https://www.kaggle.com/code/gracesampao/grace-sampao-cs-da02-25057) 
submission notebook.

----

### **The Toolkit: Logic and Structure 🛠️**

My process relied on the following key tools:

* **[Python](https://www.python.org/):** The foundational language for all data 
manipulation.
* **[Pandas](https://pandas.pydata.org/docs/index.html):** The indispensable library 
for data cleaning, exploration, and manipulation.
* **[Jupyter Notebook](https://jupyter.org/):** The web application used for creating 
and sharing the computational documents.
* **[Visual Studio Code](https://code.visualstudio.com/):** My primary code editor.

----

### **The Key Takeaway: Precision in Handling Nulls and Types 💡**

The most valuable lessons learned involved making precise, informed decisions about 
how to handle data imperfections.

**1. Deciding When to Drop vs. When to Fill (Null Handling)**

* **Dropping:** Given the low number of nulls in `rating` and `date_added` (relative 
to the overall dataset size), I opted to drop the handful of rows to maintain the 
highest quality and consistency in those core fields.

* **Filling (Reinforcing):** For `director`, `cast`, and `country`, dropping nulls 
would have meant losing valuable rows. Instead, I **reinforced** the data by adding 
`"Unknown"` as a legitimate category and filling the nulls. This preserves structural 
integrity without introducing erroneous data.

```python
# Adding "Unknown" category before filling
netflix_titles["country"] = netflix_titles["country"].cat.add_categories("Unknown")

values = {"director": "Unknown", "cast": "Unknown", "country": "Unknown"}
netflix_titles.fillna(value=values, inplace=True)
```

**2. Enforcing Ordered Categorical Types**

To ensure the `rating` column was logically sound for future analysis (e.g., that 'G' 
comes before 'R'), I explicitly converted it to an **ordered categorical type** using 
a custom sequence. This ensures downstream analysis respects the non-numeric hierarchy 
of the data.

```python
from pandas.api.types import CategoricalDtype

rating_categories = CategoricalDtype(
    categories=["G", "TV-Y", "TV-G", "TV-Y7", "TV-Y7-FV", "PG", "TV-PG", "PG-13", "TV-14", "R", "TV-MA", "NC-17", "NR", "UR", ordered=True]
)

netflix_titles["rating"] = netflix_titles["rating"].astype(rating_categories)
```

----

### **Technical Challenge: Handling Multi-Category Entries 🧩**

The biggest technical challenge I faced was efficiently handling entries with multiple 
categories in columns like `country` and `listed_in`. These multi-value fields 
(where one row might contain multiple countries or genres) require more advanced 
`Pandas` techniques (like splitting and stacking) to properly normalize and prepare 
them for detailed analysis. I am confident that as I continue to develop my `Pandas` 
skills, I will master these complex data manipulation patterns.

----

### **Looking Forward: From Structural Design to Algorithmic Design 🌱**

This data wrangling project has successfully built the reliable foundation required 
for the next steps in my specialization track. The lessons learned here — especially 
about precision in data typing and thoughtful handling of missing values — will be 
carried forward into more complex modeling.

I am excited to continue documenting this transition where my aptitude for logic, 
structure, and abstract thinking is now fully dedicated to the fields of Data and 
AI. I am actively reinforcing my skills in advanced `Pandas` manipulation as I pivot 
toward algorithmic design.