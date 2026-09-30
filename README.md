# Hospital Appointment No-Show Optimization Dashboard

## 📌 Project Overview
Healthcare networks lose billions of dollars annually due to patient "no-shows"—appointments booked but completely missed without notice. This operational inefficiency delays clinical care for other patients and strains hospital resource scheduling.

This end-to-end data analytics project processes over **110,000 historic medical appointment logs** to uncover the driving behavioral patterns behind missing appointments, culminating in an executive-ready, interactive deployment dashboard.

---

## 🛠️ The Tech Stack
* **Data Source:** Automated, anonymized electronic health record (EHR) clinic logs via Kaggle.
* **Data Cleaning & Engineering:** Python (Pandas) via Google Colab.
* **Data Visualization & Analytics:** Power BI Desktop.

---

## 📈 Key Insights & Strategic Discovery
By analyzing patient records across demographics and logistics, the final dashboard revealed three high-value trends:

1. **The Forgetfulness Threshold (Wait-Times):** There is a strong direct correlation between booking lead times and no-show rates. Patients scheduled for an appointment within 48 hours show up 90% of the time, while booking lead times exceeding 15 days experience a severe spike in no-show frequencies.
2. **Young Adult Demographics:** Patients aged 18–32 represent the highest baseline demographic group skipping scheduled visits, requiring custom engagement channels compared to older age brackets.
3. **The Slicer Feature:** The interactive gender toggle highlights that behavioral scheduling friction scales globally across demographics rather than being localized to a single gender profile.

---

## 🚀 Step-by-Step Project Pipeline

### Phase 1: Python Data Cleansing
The raw EHR data contained processing anomalies, negative ages, and raw unformatted string dates. A custom script handled:
* Standardizing columns to uniform lower-case formats.
* Dropping operational errors (filtering out negative patient ages).
* Parsing string objects into proper vectorized datetime formats.
* Feature engineering a new metric: `wait_days` (Days between booking creation and actual physical appointment).

```python
# Feature Engineering snippet from script
df['scheduledday'] = pd.to_datetime(df['scheduledday'])
df['appointmentday'] = pd.to_datetime(df['appointmentday'])
df['wait_days'] = (df['appointmentday'] - df['scheduledday']).dt.days
```

### Phase 2: Power BI Dashboard Architecture
* **DAX Metric Development:** Engineered a dynamic DAX calculation measure (`No Show Percentage`) to compute real-time relative frequencies across any applied slicer filters.
* **Layout Grid Design:** Structured an intentional 4-quadrant workspace utilizing a clinical teal aesthetic to mimic enterprise-level healthcare tracking tools.
* **Interactive Elements:** Added advanced modern Button Slicers to allow operational managers to isolate insights seamlessly on demand.

---

## 💡 Operational Recommendations for Hospital Management
Based on the dashboard results, the hospital system should execute the following policies:
* **Automate Dynamic Reminders:** Implement an automated SMS text outreach engine explicitly triggered only when a patient's `wait_days` threshold crosses a 10-day buffer zone.
* **Target Mobile Outreach:** Direct mobile app notification reminders heavily at the 18–32 demographic tier to optimize engagement where text-based drops are highest.

---
*Developed as part of my professional Data Analytics Entry Portfolio.*
