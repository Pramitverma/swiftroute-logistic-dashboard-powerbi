<div align="center">

# 🚚 SwiftRoute Logistics Dashboard

### *Turning Delivery Chaos into Data-Driven Precision*

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-FF6F00?style=for-the-badge&logo=microsoft&logoColor=white)](https://docs.microsoft.com/en-us/dax/)
[![Excel](https://img.shields.io/badge/Power%20Query-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)](https://www.microsoft.com/en-us/power-platform/products/power-query)

**[Live Dashboard](#) • [Documentation](#project-structure) • [Report Issues](#)**

![Dashboard Preview]<img width="1270" height="748" alt="image" src="https://github.com/user-attachments/assets/d112dc3d-36c4-4a76-8648-ccb0f9651389" />


*A comprehensive business intelligence solution for logistics operations analysis*

---

</div>

## 📊 Project Overview

SwiftRoute Logistics Dashboard is an end-to-end **Power BI analytical solution** designed to transform raw logistics data into actionable business intelligence. This project demonstrates advanced data modeling, DAX calculations, and interactive visualization techniques to solve real-world supply chain challenges.

### 🎯 The Challenge

A logistics company managing **6 distribution hubs**, **55 drivers**, and **45 vehicles** was struggling with:
- ❌ Only **78.6%** on-time delivery rate
- ❌ No visibility into driver performance patterns
- ❌ **26.67%** of fleet sitting in maintenance
- ❌ Unclear hub efficiency metrics
- ❌ Reactive rather than proactive decision-making

### ✅ The Solution

A multi-dimensional Power BI dashboard that provides:
- 📈 Real-time KPI tracking across all operational metrics
- 🔍 Drill-through capabilities from executive overview to individual driver performance
- 🎯 Predictive insights for fleet maintenance and capacity planning
- 📊 Comparative analysis across hubs, drivers, and vehicle types
- ⚡ Automated data refresh and dynamic filtering

---

## 🌟 Key Features

<table>
<tr>
<td width="50%">

### 📍 Multi-Page Dashboard
- **Main Dashboard**: Executive KPIs and trends
- **Driver Analytics**: Performance deep-dive
- **Hub Operations**: Capacity and efficiency metrics
- **Fleet Management**: Vehicle utilization and maintenance

</td>
<td width="50%">

### 🎨 Interactive Visualizations
- Dynamic filtering across all pages
- Cross-highlighting and drill-through
- Custom tooltips with contextual data
- Mobile-optimized layouts

</td>
</tr>
</table>

### 🔥 Advanced Analytics Implemented

```dax
// Example: On-Time Delivery Rate Calculation
On Time Delivery Rate = 
DIVIDE(
    CALCULATE(COUNT(Orders[Order ID]), Orders[Is On Time] = TRUE),
    COUNT(Orders[Order ID]),
    0
)

// Driver Delay Percentage with Context
Driver Delay % = 
VAR DelayedOrders = CALCULATE(COUNT(Orders[Order ID]), Orders[Is Delayed] = TRUE)
VAR TotalOrders = COUNT(Orders[Order ID])
RETURN DIVIDE(DelayedOrders, TotalOrders, 0)

// Hub Performance Ranking
Hub Performance Rank = 
RANKX(
    ALL(Hubs[HubName]),
    [On Time Delivery Rate],
    ,
    DESC,
    Dense
)
```

---

## 📈 Insights Uncovered

<details>
<summary><b>🎯 Operational Performance Metrics</b></summary>

| Metric | Value | vs Previous Month |
|--------|-------|-------------------|
| **Total Orders** | 1,174 | +0.34% ↗️ |
| **On-Time Delivery** | 78.60% | -0.6% ↘️ |
| **CSAT Score** | 82.6% | -1.16% ↘️ |
| **Avg Delivery Time** | 36.28 hrs | +4.47% ↗️ |

**Key Finding**: Delivery times increasing while on-time rate declining - indicates systematic bottleneck.

</details>

<details>
<summary><b>🏢 Hub Performance Analysis</b></summary>

**Top Performing Hubs:**
1. 🥇 **San Antonio Hub** - 82.9% efficiency
2. 🥈 **Fort Worth Hub** - 82.1% efficiency
3. 🥉 **El Paso Hub** - 81.5% efficiency

**Underperforming:**
- ⚠️ **Austin Hub** - 72.4% (improvement opportunity)
- ⚠️ **Houston Hub** - 75.6% (highest capacity, lowest efficiency)

**Insight**: Houston processes most orders (380 capacity) but has efficiency issues - likely understaffed or process inefficiencies.

</details>

<details>
<summary><b>👥 Driver Performance Intelligence</b></summary>

**Experience vs Performance Correlation:**
- Drivers with 6+ years experience: **4.2 avg rating**
- Drivers with <3 years experience: **3.1 avg rating**
- Sweet spot: **4-7 years** = optimal performance

**Critical Action Items:**
- 🚨 **Mary Rodriguez**: 45.5% delay rate (immediate coaching needed)
- 🚨 **Michael Williams**: 43.8% delay rate
- 🚨 **Sarah Brown**: 42.9% delay rate

**Success Stories:**
- ⭐ **Matthew Wilson**: 31.6% delay rate (lowest)
- ⭐ **Barbara Garcia**: 31.6% delay rate

</details>

<details>
<summary><b>🚗 Fleet Optimization Insights</b></summary>

**Fleet Status:**
- ✅ Active Vehicles: **33 (73.33%)**
- 🔧 In Maintenance: **12 (26.67%)**

**High-Performing Models:**
- **Mercedes Sprinter**: 47 orders (highest utilization)
- **Ford Transit**: 40 orders
- **Chevrolet Express**: 25 orders

**Fleet Composition:**
- 🚚 Trucks: **64.74%** of fleet
- 🚐 Vans: **22.91%**
- 🛻 Pickups: **8.01%**
- 📦 Box Trucks: **4.34%**

**Maintenance Alert**: Vehicles averaging **6+ years** showing **2.3x higher** breakdown rates.

</details>

---

## 🗂️ Project Structure

```
SwiftRoute-Logistics-Dashboard/
│
├── 📊 Dashboard/
│   ├── SwiftRoute_Dashboard.pbix          # Main Power BI file
│   ├── SwiftRoute_Dashboard_Mobile.pbix   # Mobile-optimized version
│   └── Templates/
│       └── Report_Template.pbit           # Reusable template
│
├── 📁 Data/
│   ├── Raw/
│   │   ├── Drivers.csv                    # Driver information (55 records)
│   │   ├── Hubs.csv                       # Hub details (6 hubs)
│   │   ├── Orders.csv                     # Order transactions (1,174 orders)
│   │   └── Vehicles.csv                   # Vehicle fleet data (45 vehicles)
│   │
│   └── Processed/
│       └── DataModel.xlsx                 # Cleaned and transformed data
│
├── 📸 Screenshots/
│   ├── dashboard_main.png
│   ├── drivers_overview.png
│   ├── hubs_overview.png
│   └── vehicles_overview.png
│
├── 📝 Documentation/
│   ├── Data_Dictionary.md                 # Column definitions and descriptions
│   ├── DAX_Measures.md                    # All DAX formulas with explanations
│   ├── Power_Query_Steps.md               # Data transformation documentation
│   └── User_Guide.pdf                     # End-user manual
│
├── 🔧 Scripts/
│   └── data_generation.py                 # Sample data generator (if needed)
│
├── README.md                              # You are here!
├── LICENSE                                # MIT License
└── .gitignore                             # Git ignore file
```

---

## 🛠️ Technical Implementation

### Data Modeling Architecture

```
┌─────────────┐
│   Orders    │◄─────┐
│  (Fact)     │      │
└─────────────┘      │
       │             │
       │ 1:Many      │
       ▼             │
┌─────────────┐      │
│   Drivers   │      │
│ (Dimension) │      │
└─────────────┘      │
                     │ 1:Many
┌─────────────┐      │
│    Hubs     │◄─────┘
│ (Dimension) │
└─────────────┘
       ▲
       │ 1:Many
       │
┌─────────────┐
│  Vehicles   │
│ (Dimension) │
└─────────────┘
```

**Relationship Type**: Star Schema  
**Cardinality**: One-to-Many relationships from dimension to fact table  
**Cross-Filter Direction**: Single direction for optimal performance

---

## 🚀 Getting Started

### Prerequisites

- **Power BI Desktop** (Latest version recommended)
- **Windows 10/11** or **Power BI Service** access
- Basic understanding of DAX and Power Query

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/swiftroute-logistics-dashboard.git
   cd swiftroute-logistics-dashboard
   ```

2. **Open the Power BI file**
   ```
   Dashboard/SwiftRoute_Dashboard.pbix
   ```

3. **Refresh data connections**
   - Go to Home → Transform Data → Data Source Settings
   - Update file paths to match your local directory
   - Click "Refresh" to load data

4. **Explore the dashboard!** 🎉

---

## 📊 Dashboard Pages Overview

### 1️⃣ Main Dashboard
**Purpose**: Executive-level overview of key performance indicators

**Key Metrics Displayed:**
- Total Orders with MoM trend
- On-Time Delivery Rate with target comparison
- CSAT % with historical trend
- Average Delivery Time with benchmark

**Visualizations:**
- Hub capacity vs actual orders (bar chart)
- Hub performance ranking (horizontal bar)
- Driver experience vs ratings (scatter plot)
- Top delay drivers (bar chart)
- Vehicle distribution by model (bar chart)
- Active vs maintenance vehicles (donut chart)

---

### 2️⃣ Drivers Overview
**Purpose**: Deep-dive into individual driver performance

**Features:**
- Driver selection dropdown
- Individual driver profile card
- Monthly performance trend line
- Experience vs rating correlation
- Delay percentage ranking

**Use Cases:**
- Identify training opportunities
- Recognize top performers
- Coach underperforming drivers
- Plan resource allocation

---

### 3️⃣ Hubs Overview
**Purpose**: Hub efficiency and capacity planning

**Features:**
- Orders processed vs hub capacity
- Hub performance ranking
- Processing time heatmap by day of week
- Workload distribution analysis

**Use Cases:**
- Balance workload across hubs
- Identify capacity constraints
- Optimize staffing schedules
- Plan expansion decisions

---

### 4️⃣ Vehicles Overview
**Purpose**: Fleet management and maintenance planning

**Features:**
- Active vs maintenance status
- Vehicle age and breakdown correlation
- Orders by vehicle model
- Vehicle code breakdown analysis
- Fleet composition by type

**Use Cases:**
- Predict maintenance needs
- Plan vehicle retirement/acquisition
- Optimize fleet utilization
- Track total cost of ownership

---

## 🎓 Learning Outcomes

Building this dashboard taught me:

✅ **Advanced DAX**: Time intelligence, context transition, iterator functions  
✅ **Data Modeling**: Star schema design, relationship optimization  
✅ **Power Query**: M language, data transformation, error handling  
✅ **UX Design**: Information hierarchy, color psychology, accessibility  
✅ **Performance Optimization**: Query folding, measure optimization, aggregations  
✅ **Business Intelligence**: Translating data into actionable insights  

---

## 🔮 Future Enhancements

- [ ] **Real-time Integration**: Connect to live SQL database
- [ ] **Predictive Analytics**: ML models for delivery time prediction
- [ ] **Route Optimization**: Geographic mapping with optimal routes
- [ ] **Cost Analysis**: Fuel, maintenance, and operational cost tracking
- [ ] **Customer Feedback**: Sentiment analysis from delivery reviews
- [ ] **Mobile App**: Power Apps integration for driver check-ins
- [ ] **Automated Alerts**: Email notifications for KPI thresholds
- [ ] **Weather Integration**: Impact of weather on delivery times

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/AmazingFeature`)
3. **Commit your changes** (`git commit -m 'Add some AmazingFeature'`)
4. **Push to the branch** (`git push origin feature/AmazingFeature`)
5. **Open a Pull Request**

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct.

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Pramit Verma**

- 📧 Email: pratapverma14810869@gmail.com
- 💼 LinkedIn: [Connect with me]www.linkedin.com/in/pramit-verma-589077245
- 🐱 GitHub: [@yourusername](https://github.com/Pramitverma)
- 📊 Portfolio: [View my work](https://yourportfolio.com)

---

## 🙏 Acknowledgments

- Power BI community for inspiration and best practices
- Microsoft documentation for technical guidance
- Open-source data visualization libraries
- All the logistics professionals who provided domain insights

---

## 📸 Dashboard Screenshots

<details>
<summary><b>Click to view dashboard screenshots</b></summary>

### Main Dashboard
![Main Dashboard](Screenshots/dashboard_main.png)

### Drivers Overview
![Drivers Overview]<img width="1274" height="742" alt="image" src="https://github.com/user-attachments/assets/6c1a5d93-bece-44a3-ae67-4fbbebef8d89" />


### Hubs Overview
![Hubs Overview]<img width="1270" height="745" alt="image" src="https://github.com/user-attachments/assets/5377f9c6-6b64-468f-ac8e-08160fa5a046" />


### Vehicles Overview
![Vehicles Overview](Screenshots/vehicles_overview.png)

</details>

---

## 💡 Key Takeaways

> *"This project proves that even simple CSV files can unlock profound business insights when analyzed with the right tools and mindset. The gap between data and decision-making isn't technical—it's analytical thinking."*

---

<div align="center">

### ⭐ If this project helped you, please give it a star!

**Made with ❤️ and lots of ☕**

[![GitHub stars](https://img.shields.io/github/stars/yourusername/swiftroute-logistics-dashboard?style=social)](https://github.com/yourusername/swiftroute-logistics-dashboard/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/yourusername/swiftroute-logistics-dashboard?style=social)](https://github.com/yourusername/swiftroute-logistics-dashboard/network/members)
[![GitHub watchers](https://img.shields.io/github/watchers/yourusername/swiftroute-logistics-dashboard?style=social)](https://github.com/yourusername/swiftroute-logistics-dashboard/watchers)

---

**[⬆ Back to Top](#-swiftroute-logistics-dashboard)**

</div>
