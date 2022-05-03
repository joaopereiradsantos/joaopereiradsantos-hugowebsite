---
# An instance of the Experience widget.
# Documentation: https://wowchemy.com/docs/page-builder/
widget: experience

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 30

title: Experience
subtitle:

# Date format for experience
#   Refer to https://wowchemy.com/docs/customization/#date-format
date_format: Jan 2006

# Experiences.
#   Add/remove as many `experience` items below as you like.
#   Required fields are `title`, `company`, and `date_start`.
#   Leave `date_end` empty if it's your current employer.
#   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.
experience:
  - title: Business Intelligence Intern | Transportation & Supply Chain (EU IXD)
    company: Amazon
    company_url: 'https://amazon.com/'
    company_logo: amazon
    location: Luxembourg, Luxembourg
    date_start: '2021-02-08'
    date_end: '2021-07-31'
    description: |2-
      **[Why Spread is Biased & How to Overcome it: Spread Bias](https://drive.corp.amazon.com/documents/mznjoao@/Archive/Docs/Why%20Spread%20is%20Biased%20and%20How%20to%20Overcome%20It%20-%20Spread%20Bias.html)**
      - Development of a new metric: Spread Bias. A complementary metric to FC Spread (how many FCs on average an ASIN is sent to). Mathematically, it’s a weekly weighted average share of total volume cross-docked at each FC per ASIN. The more biased the volume is towards one particular FC, the more the spread bias will tend to 1. Reciprocally, the more evenly and the more FCs the volume is spread to, spread bias will tend towards 0;
      - Spread Bias is [] x more correlated to deviations in Case Break than in FC Spread. Less Spread Bias leads to a more uniform FC level placement which, in turn, increases unique inventory and reduces the risk of TRB (constraint in outbound capacity);
      - Semi-Automated Jupyter Notebook Code & Markdown paper with interactive .html python code preview and Plotly graphs, Placement Impact bridge with Pearson Correlation Analysis and SQL script for production use.

      **[ITS 2% Rule & Impact on Placement](https://drive.corp.amazon.com/documents/mznjoao@/Archive/Docs/IXD%202%20%25%20Rule%20and%20Impact%20on%20Placement.pdf)**
      - Understanding of hard constrains in optimization models (SCOT heuristic approach to reduce latency of the request easing the algorithm decision time by removing the possibility of case break) and impact on placement and financial outcomes (spread, item selection, period 1/ period 2 AR share and misplacement volume);
      - Expected a yearly decrease of 4MM units in total cross-border fulfillment (CBF) by reduction in misplaced volume, 3x more item selection leading to higher LIS, higher inventory turns and 2x less Spread Bias;
      - Semi-Automated Jupyter Notebook Code & Markdown paper with interactive .html python code preview and interactive Plotly graphs.    

      **[Tote Utilization Dashboard](https://eu-west-1.quicksight.aws.amazon.com/sn/dashboards/359cfee0-7325-4dcc-81d0-93e1f503171d)**
      - Tote Utilization dashboard and monitoring for the IXD Sr. Ops Managers & Area Managers. Aimed at knowledge sharing and improved users tote filling best practices in order to increase truck fill rate and tote optimization;
      - Expected an increase of 2% in the weekly average tote utilization by IXD, leading to a yearly reduction of [] MM totes, 1k trucks, 800 tonnes of CO<sub>2</sub> emissions and $ 1MM in overall savings;
      - Data Pipeline between 2 AWS RedShift Clusters, Daily Maintenance of 6 Tables with SQL ETL Manager and AWS QuickSight.       

      **[Arc Bin Level Forecast](https://eu-west-1.quicksight.aws.amazon.com/sn/dashboards/6b6d4996-87b8-4385-9782-63149627913f)**
      - Improved accuracy on the arc bin level forecast with univariate multi forecasting time series using Exponential Moving Average (EMA), Auto-ARIMA and FBProphet models. QuickSight analysis and Dashboard for the preceding weekly arc bin volume and share;
      - 5% increase in forecast accuracy leading to an expected optimization in bin level planning for bin fullness balance and IXD bin offsets;
      - AWS SageMaker with Python: Pandas, Matplotlib, NumPy, Pmdarima and FBProphet, AWS RedShift and AWS QuickSight.        

      <b>Centralized Fluid Loading Dashboard</b>
      <details><summary>Details</summary>
      <a href="https://drive.corp.amazon.com/documents/mznjoao@/Archive/Docs/IXD%20Sort%20Share%20and%20Impact%20on%20Placement.pdf">Internal Dashboard</a>
      <ul>
        <li>Centralized Fluid Loading (FL) Dashboard for the overall Productivity (fluid loading share, volume, fill rate and labor) Sustainability (saved number of trucks, CO2 emissions, plastic waste) and Savings (transportation, productivity gain, unloading cost) metrics;</li>
        <li>EU IXD Fluid Loading is 100% more productive than normal pallet building and loading, loads 100% more items and reduces 50% of the trucks hence saving 13.5k tonnes of CO2 emissions;</li>
        <li>SQL Scheduled Extract Jobs and Microsoft Power BI: Waffle chart, Sankey diagram & Radar chart.</li>
      </ul> 
      </details>

      <details><summary><b>Sort Share and Impact on Item Selection</b></summary>
      <a href="https://drive.corp.amazon.com/documents/mznjoao@/Archive/Docs/IXD%20Sort%20Share%20and%20Impact%20on%20Placement.pdf">Internal Documentation</a>
      <ul>
        <li>Deep dive analysis regarding the impact on the unique item selection based on the IXD sort share deviation to ideals. Financial outcome based on the country level Cross-Border Fulfillment (CBF) cost on different ITS algorithm decisions;</li>
        <li>Improved sort share bridge to item selection and weekly WBR review in sort share deviation to ideals, right sortation and CBF due to wrong sortation;</li>
        <li>SQL Extract Jobs and Statistical Analysis with Excel: Pearson Correlation Coefficient, P-Value and Linear Regression.</li>
      </ul> 
      </details>


  - title: Data Analyst Intern | Physical Failure Analysis & Reliability Lab
    company: Amkor Technology
    company_url: "https://amkor.com/"
    company_logo: amkor_tech
    location: Mindelo, Portugal
    date_start: "2020-09-01"
    date_end: "2021-01-11"
    description: |2-
      <b>Requests Management Workflow Automation & Optimization</b>
      <details><summary>Details</summary>
      <ul>
        <li>Applied DMAIC methodology (Define, Measure, Analyze, Improve, and Control) as a data-driven improvement cycle to clearly articulate the business problem, goal, potential resources, project scope, and high-level project timeline. Aimed at improving the Request Scheduling Efficiency by over 48% in a year;</li>
        <li>Implemented and Tracked KPIs with Python: Pandas, Statsmodels, Seaborn and Plotly;</li>
        <li>Semi-Automated a Relative Job Prioritization System with Excel: Power Query and VBA;</li>
        <li>Dashboard Prototype with Python: Dash and User Adoption with a Macro-Enabled Workbook.</li>
      </ul> 
      </details>

  - title: Master Thesis Project | Process Engineer
    company: Amkor Technology
    company_url: "https://amkor.com/"
    company_logo: amkor_tech
    location: Mindelo, Portugal
    date_start: "2020-02-01"
    date_end: "2020-08-01"
    description: |2-
      **Qualitative and Quantitative Statistical Analysis in Copper Electroplating Baths**
      - Applying linear regression and correlation models (Pearson and Spearman) with R, Minitab and Excel, easing the decision-making process associated with the control of the main chemical components concentrations and total organic contaminations (TOC);
      - Extract, Transform and Load (ETL) process applied to past manufacturing datasets, implemented on the Business Intelligence and Analytics software platform Microsoft Power BI, retrieving valuable insights.
  
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus imperdiet, nulla et dictum interdum, nisi lorem egestas vitae scel<span id="dots">...</span><span id="more">erisque enim ligula venenatis dolor. Maecenas nisl est, ultrices nec congue eget, auctor vitae massa. Fusce luctus vestibulum augue ut aliquet. Nunc sagittis dictum nisi, sed ullamcorper ipsum dignissim ac. In at libero sed nunc venenatis imperdiet sed ornare turpis. Donec vitae dui eget tellus gravida venenatis. Integer fringilla congue eros non fermentum. Sed dapibus pulvinar nibh tempor porta.</span></p>
      <button onclick="myFunction()" id="myBtn">Read more</button> 

design:
  columns: '2'
---
