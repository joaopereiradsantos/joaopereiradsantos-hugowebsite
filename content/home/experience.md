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
  - title: Business Intelligence Engineer II | Transportation & Supply Chain (EU SC FC Launch & Transfer Analytics)
    company: Amazon
    company_url: 'https://amazon.com/'
    company_logo: amazon
    location: Barcelona, Spain
    date_start: '2023-04-01'
    date_end: 
    description: |2-
      <p><b>EU Supply Chain Analytics FC Launch</b><br> 
      The <a href="https://w.amazon.com/bin/view/EU_SC_FC_Launch_Transfer_Analytics/">EU SC FC Launch Team</a> manages the supply chain ramp up of new Amazon-owned FCs from zero to one. The team strives to support the overall S-Team goal of 10% YoY productivity improvement of new FCs by providing required IB and OB daily/weekly volumes to maximize new FC's operation effciency.</p>
      <br>
      <ul>

        <li>
          <b>EU SC Network Planning MBR Tech Lead</b>
          <p>Led the EU SC Network Planning Tech MBR, coordinating 5 subteams across 25 tech projects. Collaborated closely with 5 tech members and 5 business stakeholders, orchestrating the successful delivery of solutions
        </li>


  - title: Business Intelligence Engineer | Transportation & Supply Chain (EU SC FC Launch & Transfer Analytics)
    company: Amazon
    company_url: 'https://amazon.com/'
    company_logo: amazon
    location: London, United Kingdom
    date_start: '2021-08-01'
    date_end: '2023-04-01'
    description: |2-
      <p><b>EU Supply Chain Analytics Data Engineering Admin</b><br> 
      The <a href="https://w.amazon.com/bin/view/EU_SC_ANALYTICS_BI_ADMIN/">EU SC Analytics Data Engineering Admin Team</a> mission is to empower the users (+300 users) to produce and obtain data in the fastest, easiest and cheapest way, while maintaining and continuously improve the data infrastructure.<br>
      Ownership and management of 2 AWS accounts, including 2 Redshift clusters.</p>
      <br>
      <ul>

        <li>
          <b>EXTREME: Excel to Redshift Migration Engine</b>
          <p>A Native AWS solution that automatically converts your .xlsx files into Redshift local tables seamlessly and quickly while additionally inferring the most frugal table definition based on the present data.
          <details><summary>Details</summary>
          <a href="https://w.amazon.com/bin/view/EXTREME/">Internal Documentation</a>
          <ul>
            <li>EXTREME is centered around a micro-service orchestration workflow using AWS Step Functions. It was designed for the best user-experience by only requiring minimal knowledge on basic tools and functionalities using Excel and Network Shared Folders. Drop your Excel file inside the appropriate sub folder, wait and get notified on the EXTREME Chime room once the table has been Created or Updated on EUSOPDW.</li>
            <img src="https://joaopereiradsantos.com/uploads/extreme_userdiag.png" alt="EXTREME User Architecture">
            <img src="https://joaopereiradsantos.com/uploads/stepfunctions_graph.png" alt="EXTREME SF Diagram">
          </ul> 
          </details></p>
        </li>

        <li>
          <b>AWS EUSOPDW CloudWatch Dashboard</b>
          <p>Leverage the power of CloudWatch metrics into EUSOPDW Redshift cluster to develop the EUSOPDW CloudWatch Dashboard. Using CloudWatch metrics for Amazon Redshift, we can get information about the cluster's health and performance up to the node level. 
          <details><summary>Details</summary>
          <a href="https://w.amazon.com/bin/view/EU_SC_ANALYTICS_BI_ADMIN/Redshift_Cloudwatch/">Internal Dashboard</a>
          <ul>
            <li>EUSOPDW CloudWatch Dashboard monitors the real time performance of EUSOPDW cluster across multiple metrics, e.g. the average query completion time, the number of queries running or the number of queries waiting.</li>
            <li>The EU SC Analytics BI Admin Team have also implemented 4 metric alarms in order to proactively act on cluster issues, e.g. high backlog or unusual CPU utilization.</li>
            <li>The Dashboard is divided into 3 main section: 1 – Overview: Focus on 3 main metrics (WLMQueryDuration, WLMRunningQueries and WLMQueueLength) on the 3 main WLM Queues (admin, allusers and planners); 2 – Performance: Focus mainly on CPU utilization per node, network and I/O rates, open DB connections and query stage share; 3 – WLM Performance and Latency Performance: Similar to the Overview section but with more metric details and all the existing WLM Queues and latency granularity (short, medium and long).</li>
            <img src="https://joaopereiradsantos.com/uploads/rs_cloudwatch_1.png" alt="Redshift CloudWatch 1">
            <img src="https://joaopereiradsantos.com/uploads/rs_cloudwatch_2.png" alt="Redshift CloudWatch 2">
          </ul> 
          </details></p>
        </li>

        <li>
          <b>AWS Auto Tag</b>
          <p>“Tag Early, Tag, Often”. Automatically tagging resources greatly improves the ease of cost allocation and governance by the BI Admin Team. It is a challenge to get users to remember to and correctly label every AWS resource. Fundamentally they shouldn’t have to. 
          <details><summary>Details</summary>
          <a href="https://github.com/GorillaStack/auto-tag">Public Documentation</a>
          <ul>
            <li>As soon as a user creates a resource supported by AutoTag (such as EC2 instances, IAM users, IAM roles, RDS instances, S3 buckets, EMR clusters, VPCs, etc), AutoTag will automatically apply up to 3 new tags: C (Resource Owner) + T (Resource Creation Datetime) + I (Resource Invoked by what other resource).</li>
          </ul> 
          </details></p>
        </li>

        <li>
          <b>AWS Auto Scheduler</b>
          <p>Reduces operational costs by stopping resources that are not in use and starts resources when their capacity is needed. This solution can result in up to 70% cost savings on those instances that are only necessary during regular business hours (weekly utilization reduced from 168 hours to 50 hours). 
          <details><summary>Details</summary>
          <a href="https://docs.aws.amazon.com/solutions/latest/instance-scheduler-on-aws/welcome.html">Public Documentation</a>
          <ul>
            <li>Simply tag the key as “AutoSchedule” and associate the respective scheduler value (i.e. Key = “AutoSchedule”; Value = “1130-only-stop”);</li>
            <li>Schedule configurations are set using the AutoScheduler-ConfigTable on DynamoDB. A user can create a period (i.e. office-hours: starts at 09:00, ends at 17:00 during week days) and then create a schedule based on a single or multiple periods (i.e. using the previous office-hours period but adding the timezone: Europe/London);</li>
            <li>Configuration setup also allows for vertical scaling: scale up or down based on the instance requirements (i.e. scale up an instance to t2.micro during weekends and scale down to t2.nano during the week).</li>
          </ul> 
          </details></p>
        </li>

        <li>
          <b>AWS Sagemaker Auto Stop</b>
          <p>Sagemaker is the second largest cost in our AWS accounts. This solution auto-shutdown both SageMaker Notebook and SageMaker Studio instances when they are idle for 1 hour. 
          <details><summary>Details</summary>
          <a href="https://github.com/aws-samples/amazon-sagemaker-notebook-instance-lifecycle-config-samples/blob/master/scripts/auto-stop-idle/autostop.py">Public Documentation</a>
          <ul>
            <li>A lifecycle configuration provides shell scripts that run either when a notebook instance is created or whenever it starts. The deployed lifecycle config will run the autostop.py module every 5 minutes on the backend;</li>
            <li>It will be making API calls to the Jupyter server and checking the kernel status for ‘idle’. ‘Idleness’ as defined by Jupyter team, means that no code is running (other activities such as opening a new notebook will also reset the idle timer).</li>
          </ul> 
          </details></p>
        </li>
        </ul>

      <p><b>EU Supply Chain Analytics FC Launch</b><br> 
      The <a href="https://w.amazon.com/bin/view/EU_SC_FC_Launch_Transfer_Analytics/">EU SC FC Launch Team</a> manages the supply chain ramp up of new Amazon-owned FCs from zero to one. The team strives to support the overall S-Team goal of 10% YoY productivity improvement of new FCs by providing required IB and OB daily/weekly volumes to maximize new FC's operation effciency.</p>
      <br>
      <ul>

        <li>
          <b>Tech Project Manager & Mentor</b>
          <p>Manage a team of 5+ BI interns by applying Agile project management methodologies (Scrum & Kanban) on <a href="https://app.asana.com/">Asana</a>. Enforce software development good practices (<a href="https://git-scm.com/">git</a> for version control, <a href="https://github.com/pyenv/pyenv">pyenv</a> for Python version management and <a href="https://python-poetry.org/">poetry</a> for Python packaging and dependency management). 
          <details><summary>Details</summary>
          <a href="https://app.asana.com/0/portfolio/1201494474767093/list">Internal Documentation</a>
          <ul>
            <li>Setup documentation and provide support for new tech users ramp-up;</li>
            <li>Mentor and enpower BI interns for a successful career and experience;</li>
            <li>Manage technical projects on Asana based on Project Managers (PM) requirements. Break down the problem statement, set-up tasks and assign relative priorities, due dates and estimated completion times. Code review the merge requests (MR), main branch merging and production deployment (CI/CD);</li>
            <li>Impose a standardised code-style, formatter and linter (XML for SQL and <a href="https://github.com/psf/black">black</a> and <a href="https://flake8.pycqa.org/en/latest/">flake8</a> for IDE). Use of <a href="https://chaseonsoftware.com/most-common-programming-case-types/#snake_case">snake_case</a> for functions and variables and <a href="https://chaseonsoftware.com/most-common-programming-case-types/#pascalcase">PascalCase</a> for classes. Use of <a href="https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html">Google Style</a> for docstrings. TOML for configuration files to be read by humans, JSON for machines;</li>
            <li>Enforce data pipelines documentation and <a href="https://pyramid.corp.amazon.com/">Pyramid</a> (internal tool as a scalable way of tracking the status and tracing upstream pipelines) enabled alerts for proactive monitoring and management of production-ready team pipelines.</li>
          </ul> 
          </details></p>
        </li>

        <br>

        <li>
          <b>Pod Selection Algorithm</b>
          <p>Output a list of pods to transfer based on a set of inputs, business criteria (objective functions) and hard operational constrains. The objective functions currently set are: Cube (SUM volume [ft2] of each unit in a pod); Uniqueness (Count of distinct ASINs in a pod that are unique relative to their presence within their respective marketplace); Quantity (SUM units in a pod). 
          <details><summary>Details</summary>
          <a href="https://gitlab.aws.dev/eu-sc-fc-launches-transfer-analytics-tech/pod-selection-algorithm">Internal Repository</a> | 
          <a href="https://drive.corp.amazon.com/documents/mznjoao@/Archive/EUSCAnalyticsFCLaunch_PSA.pdf">Internal Documentation</a>
          <ul>
            <li>The core modeling started as a Nested Sorting optimization but migrated to a Integer Linear Programming (ILP) optimization using the FICO Xpress Solver. While the core mathematical concepts remain, as opposed to achieve a single optimal output, PSA uses a weights tunning approach for every new set of inputs simulating 1k+ data points for different weight and objective function combinations;</li>
            <li>While the previous production model (SPOCK) produced an overall weekly weighted average of 33 cube per pod (CPP), PSA generated 36 CPP (~10% improvement). Fullness of all pods transferred is on average 105% instead of 90%. Similarly, the actual weekly weighted average units per pod (UPP) was 550 while PSA’s UPP equaled 420 (~15% decrease), which reduces OB NWA because of less inventory units. PSA really stands out when it comes to unique inventory: SPOCK logic transferred 140k unique units, totaling 7% with respect to the total transferred units, while PSA transferred 45k, 2% versus the total transferred units (500bps reduction).</li>
          </ul> 
          </details></p>
        </li>

        <br>

        <li>
          <b>Pre-Launch TSO Max Capacity Alert & Automated CPT Closure</b>
          <p>Automated control on pre-launch TSO assigments for new FC launches. Gets live TSO from RODEO, updates a Chime room based on the predefined FC processing capacity threshold for a given source FC, destination FC and CPT and applies a RTCT Closure once 95% TSO capacity is breached.
          <details><summary>Details</summary>
          <a href="https://gitlab.aws.dev/eu-sc-fc-launches-transfer-analytics-tech/max-tso-alert-rtct-closure">Internal Documentation</a>
          <ul>
            <li>Pre-launch TSO is only available for unique inventory stranded in the new FC while outbound systems are still not live. It allows for a better customer promise but is highly risky as it directly impacts customer experience if the FC processing capacity vs TSO assignments per CPT is inadequate;</li>
            <li>There are 4 notification bins per CPT: 75-85%, 85-95%, 95-100% and +100%. The automated capping will trigger at +95%. In order to avoid triggering at every run, a log file is updated only triggering the alert once per bin;</li>
            <li>The script interacts with internal supply chain systems APIs to retrieve current arc assignments ready to be picked and arc scheduling and configurations in order to cap the CPT. Deployed on a EC2/ Amazon Linux 2 CloudDevDesktop and scheduled using cron (*/5 * * * *).</li>
          </ul> 
          </details></p>
        </li>

        <br>
        
        <li>
          <b>EU SC FC Launch Performance Dashboard</b>
          <p>The EU SC FC Launch Performance Dashboard is a “One Stop Shop” metrics compilation to provide a user friendly interface and visualizations of new FC’s ramp up actuals vs. wk-1/locked S&OP plans.
          <details><summary>Details</summary>
          <a href="https://eu-west-1.quicksight.aws.amazon.com/sn/accounts/764946308314/dashboards/32833b51-28e3-4576-92ac-a756ce108c6c">Internal Dashboard</a>
          <ul>
            <li>It aims to not only support Launch PM with easy data access during pre/post launch period, but also facilitate post-mortem analysis such as comparing ramp up performance of FCs launched in different years;</li>
            <li>For each FC and Week combination there’re a different number of possible Flows and Subflows. For instance, as the main flow: Crossdock Transfer In, Inventory, Manual Transfer In, New Vendor Freight, New Workable Demand, Not Yet Received (FC Receive Correction), Orders Cancelled/ Confirmed/ Received/ Submitted, Pod Transfer In, Proactive Transfer In, Reactive Transfer In all have a respective subflow related to the total number of units drilled down by: Total Quantity, Quantity FBA and Quantity AMZN (Total Quantity = FBA + AMZN);</li>
            <li>The dashboard has 7 main metric tabs (📈 TIB, NTSI, NVF, POD, INV, NWD and ORD), a summary report tab (📝 RPT), an FC comparison tab (🆚  VS) and finally a tab dedicated to our team contact information and extract/ load job details (👨‍💻 INFO).</li>
          </ul> 
          </details></p>
        </li>

  - title: Business Intelligence Intern | Transportation & Supply Chain (EU IXD)
    company: Amazon
    company_url: 'https://amazon.com/'
    company_logo: amazon
    location: Luxembourg, Luxembourg
    date_start: '2021-02-08'
    date_end: '2021-07-31'
    description: |2-
      <ul>
        <li>
          <b>Why Spread is Biased & How to Overcome it: Spread Bias</b>
          <p>Development of a new metric: Spread Bias. A complementary metric to FC Spread (how many FCs on average an ASIN is sent to). 
          <details><summary>Details</summary>
          <a href="https://drive.corp.amazon.com/documents/mznjoao@/Archive/Docs/Why%20Spread%20is%20Biased%20and%20How%20to%20Overcome%20It%20-%20Spread%20Bias.html">Internal Documentation</a>
          <ul>
            <li>Mathematically, it’s a weekly weighted average share of total volume cross-docked at each FC per ASIN. The more biased the volume is towards one particular FC, the more the spread bias will tend to 1. Reciprocally, the more evenly and the more FCs the volume is spread to, spread bias will tend towards 0;</li>
            <li>Spread Bias is [] x more correlated to deviations in Case Break than in FC Spread. Less Spread Bias leads to a more uniform FC level placement which, in turn, increases unique inventory and reduces the risk of TRB (constraint in outbound capacity);</li>
            <li>Semi-Automated Jupyter Notebook Code & Markdown paper with interactive .html python code preview and Plotly graphs, Placement Impact bridge with Pearson Correlation Analysis and SQL script for production use.</li>
          </ul> 
          </details></p>
        </li>

        <li>
          <b>ITS 2% Rule & Impact on Placement</b>
          <p>Understanding of hard constrains in optimization models (SCOT heuristic approach to reduce latency of the request easing the algorithm decision time by removing the possibility of case break) and impact on placement and financial outcomes (spread, item selection, period 1/ period 2 AR share and misplacement volume).
          <details><summary>Details</summary>
          <a href="https://drive.corp.amazon.com/documents/mznjoao@/Archive/Docs/IXD%202%20%25%20Rule%20and%20Impact%20on%20Placement.pdf">Internal Documentation</a>
          <ul>
            <li>Expected a yearly decrease of 4MM units in total cross-border fulfillment (CBF) by reduction in misplaced volume, 3x more item selection leading to higher LIS, higher inventory turns and 2x less Spread Bias;</li>
            <li>Semi-Automated Jupyter Notebook Code & Markdown paper with interactive .html python code preview and interactive Plotly graphs.</li>
          </ul> 
          </details></p>
        </li>
        
        <li>
          <b>Tote Utilization Dashboard</b>
          <p>Tote Utilization dashboard and monitoring for the IXD Sr. Ops Managers & Area Managers. Aimed at knowledge sharing and improved users tote filling best practices in order to increase truck fill rate and tote optimization.
          <details><summary>Details</summary>
          <a href="https://eu-west-1.quicksight.aws.amazon.com/sn/dashboards/359cfee0-7325-4dcc-81d0-93e1f503171d">Internal Dashboard</a>
          <ul>
            <li>Expected an increase of 2% in the weekly average tote utilization by IXD, leading to a yearly reduction of [] MM totes, 1k trucks, 800 tonnes of CO<sub>2</sub> emissions and $ 1MM in overall savings;</li>
            <li>Data Pipeline between 2 AWS RedShift Clusters, Daily Maintenance of 6 Tables with SQL ETL Manager and AWS QuickSight.</li>
          </ul> 
          </details></p>
        </li> 

        <li>
          <b>Arc Bin Level Forecast</b>
          <p>Improved accuracy on the arc bin level forecast with univariate multi forecasting time series using Exponential Moving Average (EMA), Auto-ARIMA and FBProphet models.
          <details><summary>Details</summary>
          <a href="https://eu-west-1.quicksight.aws.amazon.com/sn/dashboards/6b6d4996-87b8-4385-9782-63149627913f">Internal Dashboard</a>
          <ul>
            <li>QuickSight analysis and Dashboard for the preceding weekly arc bin volume and share;</li>
            <li>5% increase in forecast accuracy leading to an expected optimization in bin level planning for bin fullness balance and IXD bin offsets;</li>
            <li>AWS SageMaker with Python: Pandas, Matplotlib, NumPy, Pmdarima and FBProphet, AWS RedShift and AWS QuickSight.</li>
          </ul> 
          </details></p>
        </li> 

        <li>
          <b>Centralized Fluid Loading Dashboard</b>
          <p>Centralized Fluid Loading (FL) Dashboard for the overall Productivity (fluid loading share, volume, fill rate and labor) Sustainability (saved number of trucks, CO2 emissions, plastic waste) and Savings (transportation, productivity gain, unloading cost) metrics.
          <details><summary>Details</summary>
          <a href="https://drive.corp.amazon.com/documents/mznjoao@/Archive/Docs/IXD%20Sort%20Share%20and%20Impact%20on%20Placement.pdf">Internal Dashboard</a>
          <ul>
            <li>EU IXD Fluid Loading is 100% more productive than normal pallet building and loading, loads 100% more items and reduces 50% of the trucks hence saving 13.5k tonnes of CO2 emissions;</li>
            <li>SQL Scheduled Extract Jobs and Microsoft Power BI: Waffle chart, Sankey diagram & Radar chart.</li>
          </ul> 
          </details></p>
        </li> 

        <li>
          <b>Sort Share and Impact on Item Selection</b>
          <p>Deep dive analysis regarding the impact on the unique item selection based on the IXD sort share deviation to ideals. Financial outcome based on the country level Cross-Border Fulfillment (CBF) cost on different ITS algorithm decisions.
          <details><summary>Details</summary>
          <a href="https://drive.corp.amazon.com/documents/mznjoao@/Archive/Docs/IXD%20Sort%20Share%20and%20Impact%20on%20Placement.pdf">Internal Dashboard</a>
          <ul>
            <li>Improved sort share bridge to item selection and weekly WBR review in sort share deviation to ideals, right sortation and CBF due to wrong sortation;</li>
            <li>SQL Extract Jobs and Statistical Analysis with Excel: Pearson Correlation Coefficient, P-Value and Linear Regression.</li>
          </ul> 
          </details></p>
        </li> 

  - title: Data Analyst Intern | Physical Failure Analysis & Reliability Lab
    company: Amkor Technology
    company_url: "https://amkor.com/"
    company_logo: amkor_tech
    location: Mindelo, Portugal
    date_start: "2020-09-01"
    date_end: "2021-01-11"
    description: |2-
      <li>
        <b>Requests Management Workflow Automation & Optimization</b>
        <p>Aimed at improving the Request Scheduling Efficiency by over 48% YoY.
        <details><summary>Details</summary>
        <ul>
          <li>Applied DMAIC methodology (Define, Measure, Analyze, Improve, and Control) as a data-driven improvement cycle to clearly articulate the business problem, goal, potential resources, project scope, and high-level project timeline;</li>
          <li>Implemented and Tracked KPIs with Python: Pandas, Statsmodels, Seaborn and Plotly;</li>
          <li>Semi-Automated a Relative Job Prioritization System with Excel: Power Query and VBA;</li></ul>
          <li?Dashboard Prototype with Python: Dash and User Adoption with a Macro-Enabled Workbook.</li>
        </ul> 
        </details></p>
      </li> 

  - title: Master Thesis Project | Process Engineer
    company: Amkor Technology
    company_url: "https://amkor.com/"
    company_logo: amkor_tech
    location: Mindelo, Portugal
    date_start: "2020-02-01"
    date_end: "2020-08-01"
    description: |2-
      <li>
        <b>Qualitative and Quantitative Statistical Analysis in Copper Electroplating Baths</b>
        <p>Ease the decision-making process associated with the control of the main chemical components concentrations and total organic contaminations (TOC).
        <details><summary>Details</summary>
        <a href="https://repositorio-aberto.up.pt/handle/10216/132835">Public Documentation</a>
        <ul>
          <li>Applying linear regression and correlation models (Pearson and Spearman) with R, Minitab and Excel;</li>
          <li>Implemented and Tracked KPIs with Python: Pandas, Statsmodels, Seaborn and Plotly;</li>
          <li>Extract, Transform and Load (ETL) process applied to past manufacturing datasets, implemented on the Business Intelligence and Analytics software platform Microsoft Power BI, retrieving valuable insights.</li></ul>
        </ul> 
        </details></p>
      </li> 


design:
  columns: '2'
---
