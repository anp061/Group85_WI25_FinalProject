# Group85_WI25_FinalProject
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Residential and Commercial Crime Rate in Cambridge\n",
    "\n",
    "# Permissions\n",
    "\n",
    "Place an `X` in the appropriate bracket below to specify if you would like your group's project to be made available to the public. (Note that student names will be included (but PIDs will be scraped from any groups who include their PIDs).\n",
    "\n",
    "* [ X ] YES - make available\n",
    "* [  ] NO - keep private\n",
    "\n",
    "# Names\n",
    "\n",
    "- Jayminn Anand\n",
    "- Vincent Luu\n",
    "- Srikar Mannam\n",
    "- Slater Mutunga\n",
    "- Angela Perez\n",
    "\n",
    "# Abstract\n",
    "\n",
    "\n",
    "When creating our research question, we knew we wanted it to be about the crime rate, so we chose a specific type of crime, theft, and picked a time period that could be correlated with that crime. The reason we chose to limit our scope to the City of Cambridge was that we wanted to have a large enough dataset to accurately represent the crime rate within a city but not too much data from different places to the point where other factors like poverty rate, education, or weather would affect the data. We also wanted to pick an area within the U.S. since we wanted a place that would commonly celebrate Christmas, as that is one of the core considerations of our research question. We found a dataset on the City of Cambridge that fit our criteria, and we also found that it happened to have a very high crime rate compared to other cities in the U.S., so we thought it would make for an interesting point of analysis.\n",
    "\n",
    "To first get a feel for the dataset, we looked at the mean and median of the months that all crimes and theft-related crimes occurred in to see if it tended to any one side. Then, we plotted out the count of theft crimes across all months in a year for all the years within the dataset to see if there was any noticeable difference between December and the other months. Since plotting the count data fails to take into consideration the total number of crimes that happened within the months as well, we also plotted the proportion of theft-related crime to total crimes, to see if the rate of crime had any noticeable difference in December.\n",
    "\n",
    "From our data and plots, we found December did not tend to have the highest amount or rate of theft-related crimes compared to all the other months, instead it was often August that had the most for both count and proportion of theft crimes. We did notice however that December tended to have a higher count and proportion of theft-related crimes when compared to the months in Winter and Spring, which are December to June. So while December may not have had a higher crime rate compared to all the other months within a year, it did have a higher crime rate compared to other months that are in seasons of cooler climates."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Research Question"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "How do residential and commercial burglary rates in the city of Cambridge during December compare to the rest of the year from 2009-2024?\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Background and Prior Work"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Crime patterns often fluctuate based on various factors like weather or location. Our research question focuses on one of these factors, the time of year close to Christmas. We also limited the geographical scope of our research question considering that crime data is quite large and difficult to manage and analyze over a large scope. We chose a city with a sizable population that has publicly available crime data. \n",
    "\n",
    "The City of Cambridge has a population of around 118,000 people <a name=\"cite_ref-1\"></a>[<sup>1</sup>](#cite_note-1) and has a high crime rate in proportion to its population. In fact, Cambridge has a total crime index of 6, meaning it's safer than only 6% of cities in the U.S. with a property crime rate of 30.63 per 1000 residents. <a name=\"cite_ref-2\"></a>[<sup>2</sup>](#cite_note-2) In addition, since Cambridge is in America, it's likely that most people celebrate Christmas, which is critical to our research question. For these reasons, we chose Cambridge as the location of choice for our analysis.\n",
    "\n",
    "For prior research on our research question, according to a blog from DeepSentinel, U.S. burglary rates in 2023 spiked in December by 20% compared to the average monthly rate of  robbery and personal larceny. <a name=\"cite_ref-3\"></a>[<sup>3</sup>](#cite_note-3) Although the research from this blog post encapsulates a much bigger scope than our research question does, it does show that holiday theft is a real phenomenon in the U.S. as a whole, and the extent to which this affects the City of Cambridge in particular is not nearly as researched, making it worth analyzing.\n",
    "\n",
    "\n",
    "1. <a name=\"cite_note-1\"></a> [^](#cite_ref-1) Demographics and Statistics FAQ. *City of Cambridge CDD, Massachusetts*. https://www.cambridgema.gov/cdd/factsandmaps/demographicfaq  \n",
    "2. <a name=\"cite_note-2\"></a> [^](#cite_ref-2) Cambridge, MA Crime Rates and Statistics. *NeighborhoodScout*. https://www.neighborhoodscout.com/ma/cambridge/crime \n",
    "3. <a name=\"cite_note-3\"></a> [^](#cite_ref-3) Chen, WInston. (3, Dec. 2024) 'Tis the Season to prevent Holiday Crimes: A Homeowner's Guide. *Deep Sentinel*\n",
    "https://www.deepsentinel.com/blogs/tis-the-season-for-holiday-break-ins-and-package-thefts/ \n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Hypothesis\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "We hypothesize that reported residential and commercial burglaries increase by at least 10% during December compared to any other month-long periods throughout the rest of the year in the City of Cambridge. This is driven by increased holiday travel and presence of high-value items within stores and homes when Christmas is near."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Data"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Data overview\n",
    "\n",
    "- Dataset #1\n",
    "  - Dataset Name: Cambridge Crime Data\n",
    "  - Link to the dataset: https://www.kaggle.com/datasets/melissamonfared/cambridge-crime-data-2009-2024\n",
    "  - Number of observations: ~ 95,000\n",
    "  - Number of variables: 7\n",
    "  - Variable List:\n",
    "      - FileNumber: Provides a unique identifier for each observation (object/string) \n",
    "      - ReportDate: The date the crime was reported (datetime)\n",
    "      - CrimeDate: The data and time the crime occurred (object/string)\n",
    "      - Crime: Describes the type of crime that occurred (object/string)\n",
    "      - year: The year the crime occurred (int)\n",
    "      - month: The month the crime occurred (int)\n",
    "      - dec: Determines if the crime occurred in December or not\n",
    "\n",
    "\n",
    "This dataset contains reported crime incidents in the City of Cambridge and has data spanning from 2009 to 2024. This dataset provides information\n",
    "on the types of crime, when the crime occurred, and when it was reported which is needed for our research question as it is reliant on the type of crime and the date of the crime. All the datatypes are objects except for the year and time columns which are ints. It also includes data about the areas in which the crimes happened within the City of Cambridge but we will not be using that data for this analysis. The dataset is already well formatted in terms of its entries, and there are no missing values, so we will only need to remove the columns that\n",
    "we do not need for our analysis.\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Cambridge Crime Dataset"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>FileNumber</th>\n",
       "      <th>ReportDate</th>\n",
       "      <th>CrimeDate</th>\n",
       "      <th>Crime</th>\n",
       "      <th>year</th>\n",
       "      <th>month</th>\n",
       "      <th>dec</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>2009-01323</td>\n",
       "      <td>2009-02-21 09:53:00</td>\n",
       "      <td>02/21/2009 09:20 - 09:30</td>\n",
       "      <td>Threats</td>\n",
       "      <td>2009</td>\n",
       "      <td>2</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>2009-01324</td>\n",
       "      <td>2009-02-21 09:59:00</td>\n",
       "      <td>02/20/2009 22:30 - 02/21/2009 10:00</td>\n",
       "      <td>Auto Theft</td>\n",
       "      <td>2009</td>\n",
       "      <td>2</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2009-01327</td>\n",
       "      <td>2009-02-21 12:32:00</td>\n",
       "      <td>02/19/2009 21:00 - 02/21/2009 12:00</td>\n",
       "      <td>Hit and Run</td>\n",
       "      <td>2009</td>\n",
       "      <td>2</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>2009-01331</td>\n",
       "      <td>2009-02-21 15:05:00</td>\n",
       "      <td>02/21/2009 15:00 - 15:10</td>\n",
       "      <td>Larceny (Misc)</td>\n",
       "      <td>2009</td>\n",
       "      <td>2</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>2009-01346</td>\n",
       "      <td>2009-02-22 05:02:00</td>\n",
       "      <td>02/22/2009 05:02</td>\n",
       "      <td>OUI</td>\n",
       "      <td>2009</td>\n",
       "      <td>2</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>95918</th>\n",
       "      <td>2024-03755</td>\n",
       "      <td>2024-05-07 13:13:00</td>\n",
       "      <td>05/04/2024 12:00 - 18:00</td>\n",
       "      <td>Larceny from MV</td>\n",
       "      <td>2024</td>\n",
       "      <td>5</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>95919</th>\n",
       "      <td>2024-03756</td>\n",
       "      <td>2024-05-07 14:41:00</td>\n",
       "      <td>05/07/2024 14:40 - 14:41</td>\n",
       "      <td>Accident</td>\n",
       "      <td>2024</td>\n",
       "      <td>5</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>95920</th>\n",
       "      <td>2024-03777</td>\n",
       "      <td>2024-05-07 20:13:00</td>\n",
       "      <td>05/07/2024 15:00 - 19:15</td>\n",
       "      <td>Larceny of Bicycle</td>\n",
       "      <td>2024</td>\n",
       "      <td>5</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>95921</th>\n",
       "      <td>2024-03806</td>\n",
       "      <td>2024-05-08 16:09:00</td>\n",
       "      <td>05/07/2024 04:00 - 04:05</td>\n",
       "      <td>Larceny from MV</td>\n",
       "      <td>2024</td>\n",
       "      <td>5</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>95922</th>\n",
       "      <td>2024-03824</td>\n",
       "      <td>2024-05-09 10:23:00</td>\n",
       "      <td>05/05/2024 11:30 - 13:00</td>\n",
       "      <td>Hit and Run</td>\n",
       "      <td>2024</td>\n",
       "      <td>5</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>95923 rows × 7 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "       FileNumber          ReportDate                            CrimeDate  \\\n",
       "0      2009-01323 2009-02-21 09:53:00             02/21/2009 09:20 - 09:30   \n",
       "1      2009-01324 2009-02-21 09:59:00  02/20/2009 22:30 - 02/21/2009 10:00   \n",
       "2      2009-01327 2009-02-21 12:32:00  02/19/2009 21:00 - 02/21/2009 12:00   \n",
       "3      2009-01331 2009-02-21 15:05:00             02/21/2009 15:00 - 15:10   \n",
       "4      2009-01346 2009-02-22 05:02:00                     02/22/2009 05:02   \n",
       "...           ...                 ...                                  ...   \n",
       "95918  2024-03755 2024-05-07 13:13:00             05/04/2024 12:00 - 18:00   \n",
       "95919  2024-03756 2024-05-07 14:41:00             05/07/2024 14:40 - 14:41   \n",
       "95920  2024-03777 2024-05-07 20:13:00             05/07/2024 15:00 - 19:15   \n",
       "95921  2024-03806 2024-05-08 16:09:00             05/07/2024 04:00 - 04:05   \n",
       "95922  2024-03824 2024-05-09 10:23:00             05/05/2024 11:30 - 13:00   \n",
       "\n",
       "                    Crime  year  month    dec  \n",
       "0                 Threats  2009      2  False  \n",
       "1              Auto Theft  2009      2  False  \n",
       "2             Hit and Run  2009      2  False  \n",
       "3          Larceny (Misc)  2009      2  False  \n",
       "4                     OUI  2009      2  False  \n",
       "...                   ...   ...    ...    ...  \n",
       "95918     Larceny from MV  2024      5  False  \n",
       "95919            Accident  2024      5  False  \n",
       "95920  Larceny of Bicycle  2024      5  False  \n",
       "95921     Larceny from MV  2024      5  False  \n",
       "95922         Hit and Run  2024      5  False  \n",
       "\n",
       "[95923 rows x 7 columns]"
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#imports\n",
    "import pandas as pd\n",
    "import seaborn as sns\n",
    "import matplotlib.pyplot as plt\n",
    "#read and clean dataset\n",
    "df = pd.read_csv('https://raw.githubusercontent.com/vluu03/COGS108_Repo/refs/heads/main/Crime_Reports_20240701.csv')\n",
    "clean = df[['File Number','Date of Report','Crime Date Time','Crime']]\n",
    "clean = clean.rename(columns={\"File Number\":\"FileNumber\", \"Date of Report\":\"ReportDate\", \"Crime Date Time\":\"CrimeDate\"})\n",
    "clean['ReportDate'] = pd.to_datetime(clean['ReportDate']) \n",
    "clean['year'] = clean['ReportDate'].dt.year.astype(int)\n",
    "clean['month'] = clean['ReportDate'].dt.month.astype(int)\n",
    "clean['dec'] = (clean['month'] == 12)\n",
    "clean"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Results\n",
    "\n",
    "## Exploratory Data Analysis\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Filtering and Categorizing Data\n",
    "\n",
    "First, we want to see the different types of crimes that are listed in the dataset to see which ones are related to theft."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array(['Threats', 'Auto Theft', 'Hit and Run', 'Larceny (Misc)', 'OUI',\n",
       "       'Aggravated Assault', 'Commercial Break', 'Street Robbery',\n",
       "       'Housebreak', 'Shoplifting', 'Forgery', 'Simple Assault',\n",
       "       'Warrant Arrest', 'Disorderly', 'Larceny from Building',\n",
       "       'Mal. Dest. Property', 'Larceny from MV', 'Trespassing',\n",
       "       'Larceny from Person', 'Missing Person', 'Larceny from Residence',\n",
       "       'Harassment', 'Liquor Possession/Sale', 'Flim Flam', 'Phone Calls',\n",
       "       'Larceny of Bicycle', 'Annoying & Accosting', 'Drugs',\n",
       "       'Indecent Exposure', 'Larceny of Plate', 'Sex Offender Violation',\n",
       "       'Counterfeiting', 'Rec. Stol. Property', 'Commercial Robbery',\n",
       "       'Kidnapping', 'Drinking in Public', 'Larceny of Services',\n",
       "       'Peeping & Spying', 'Homicide', 'Extortion/Blackmail', 'Stalking',\n",
       "       'Weapon Violations', 'Prostitution', 'Arson', 'Embezzlement',\n",
       "       'Admin Error', 'Violation of R.O.', 'Violation of H.O.',\n",
       "       'Domestic Dispute', 'Gambling', 'Accident', 'Noise Complaint',\n",
       "       'Suspicious Package', 'Taxi Violation'], dtype=object)"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#All unique types of crimes\n",
    "unique = clean['Crime'].unique()\n",
    "unique"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Now we want to make a new column that determines if a crime was theft-related or not by filtering for certain words. We can also drop all the reports in 2024 since the dataset stopped collecting data after May."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 72,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>FileNumber</th>\n",
       "      <th>ReportDate</th>\n",
       "      <th>CrimeDate</th>\n",
       "      <th>Crime</th>\n",
       "      <th>year</th>\n",
       "      <th>month</th>\n",
       "      <th>dec</th>\n",
       "      <th>theft</th>\n",
       "      <th>res_theft</th>\n",
       "      <th>com_theft</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>1819</th>\n",
       "      <td>2009-00002</td>\n",
       "      <td>2009-01-01 00:39:00</td>\n",
       "      <td>01/01/2009 00:39</td>\n",
       "      <td>Simple Assault</td>\n",
       "      <td>2009</td>\n",
       "      <td>1</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>102</th>\n",
       "      <td>2009-00003</td>\n",
       "      <td>2009-01-01 01:34:00</td>\n",
       "      <td>01/01/2009 01:34</td>\n",
       "      <td>Simple Assault</td>\n",
       "      <td>2009</td>\n",
       "      <td>1</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>103</th>\n",
       "      <td>2009-00004</td>\n",
       "      <td>2009-01-01 01:43:00</td>\n",
       "      <td>01/01/2009 02:20 - 02:35</td>\n",
       "      <td>Aggravated Assault</td>\n",
       "      <td>2009</td>\n",
       "      <td>1</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>104</th>\n",
       "      <td>2009-00006</td>\n",
       "      <td>2009-01-01 02:34:00</td>\n",
       "      <td>01/01/2009 02:15 - 02:35</td>\n",
       "      <td>Disorderly</td>\n",
       "      <td>2009</td>\n",
       "      <td>1</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>139</th>\n",
       "      <td>2009-00008</td>\n",
       "      <td>2009-01-01 02:37:00</td>\n",
       "      <td>01/01/2009 02:37</td>\n",
       "      <td>Mal. Dest. Property</td>\n",
       "      <td>2009</td>\n",
       "      <td>1</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>92487</th>\n",
       "      <td>2023-11890</td>\n",
       "      <td>2023-12-31 12:11:00</td>\n",
       "      <td>12/31/2023 12:10</td>\n",
       "      <td>Shoplifting</td>\n",
       "      <td>2023</td>\n",
       "      <td>12</td>\n",
       "      <td>True</td>\n",
       "      <td>True</td>\n",
       "      <td>False</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>92646</th>\n",
       "      <td>2023-11894</td>\n",
       "      <td>2023-12-31 17:33:00</td>\n",
       "      <td>12/31/2023 17:33 - 17:45</td>\n",
       "      <td>Simple Assault</td>\n",
       "      <td>2023</td>\n",
       "      <td>12</td>\n",
       "      <td>True</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>92784</th>\n",
       "      <td>2023-11895</td>\n",
       "      <td>2023-12-31 18:01:00</td>\n",
       "      <td>12/31/2023 18:00</td>\n",
       "      <td>Simple Assault</td>\n",
       "      <td>2023</td>\n",
       "      <td>12</td>\n",
       "      <td>True</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>92488</th>\n",
       "      <td>2023-11897</td>\n",
       "      <td>2023-12-31 20:55:00</td>\n",
       "      <td>12/31/2023 20:45 - 21:00</td>\n",
       "      <td>Mal. Dest. Property</td>\n",
       "      <td>2023</td>\n",
       "      <td>12</td>\n",
       "      <td>True</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>92489</th>\n",
       "      <td>2023-11901</td>\n",
       "      <td>2023-12-31 22:36:00</td>\n",
       "      <td>12/31/2023 22:30 - 22:35</td>\n",
       "      <td>Simple Assault</td>\n",
       "      <td>2023</td>\n",
       "      <td>12</td>\n",
       "      <td>True</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>93164 rows × 10 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "       FileNumber          ReportDate                 CrimeDate  \\\n",
       "1819   2009-00002 2009-01-01 00:39:00          01/01/2009 00:39   \n",
       "102    2009-00003 2009-01-01 01:34:00          01/01/2009 01:34   \n",
       "103    2009-00004 2009-01-01 01:43:00  01/01/2009 02:20 - 02:35   \n",
       "104    2009-00006 2009-01-01 02:34:00  01/01/2009 02:15 - 02:35   \n",
       "139    2009-00008 2009-01-01 02:37:00          01/01/2009 02:37   \n",
       "...           ...                 ...                       ...   \n",
       "92487  2023-11890 2023-12-31 12:11:00          12/31/2023 12:10   \n",
       "92646  2023-11894 2023-12-31 17:33:00  12/31/2023 17:33 - 17:45   \n",
       "92784  2023-11895 2023-12-31 18:01:00          12/31/2023 18:00   \n",
       "92488  2023-11897 2023-12-31 20:55:00  12/31/2023 20:45 - 21:00   \n",
       "92489  2023-11901 2023-12-31 22:36:00  12/31/2023 22:30 - 22:35   \n",
       "\n",
       "                     Crime  year  month    dec  theft  res_theft  com_theft  \n",
       "1819        Simple Assault  2009      1  False  False      False      False  \n",
       "102         Simple Assault  2009      1  False  False      False      False  \n",
       "103     Aggravated Assault  2009      1  False  False      False      False  \n",
       "104             Disorderly  2009      1  False  False      False      False  \n",
       "139    Mal. Dest. Property  2009      1  False  False      False      False  \n",
       "...                    ...   ...    ...    ...    ...        ...        ...  \n",
       "92487          Shoplifting  2023     12   True   True      False       True  \n",
       "92646       Simple Assault  2023     12   True  False      False      False  \n",
       "92784       Simple Assault  2023     12   True  False      False      False  \n",
       "92488  Mal. Dest. Property  2023     12   True  False      False      False  \n",
       "92489       Simple Assault  2023     12   True  False      False      False  \n",
       "\n",
       "[93164 rows x 10 columns]"
      ]
     },
     "execution_count": 72,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "clean = clean[clean['year'] != 2024]\n",
    "clean['theft'] = clean['Crime'].str.contains('Theft|Shoplifting|Robbery|Housebreak|Larceny')\n",
    "clean['res_theft'] = clean['Crime'].str.contains('Housebreak|Building|Person|Residence|Street')\n",
    "clean['com_theft'] = clean['Crime'].str.contains('Commercial|Shoplifting')\n",
    "clean = clean.sort_values(by='ReportDate')\n",
    "clean"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "These columns will help us in the rest of the EDA section by giving us an easy way to tell whether a crime was theft-related or not and if they were residential or commercial. This gives an idea of how many of each of these crimes there are so we can filter out anything that isn't crime-related."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Residential Theft Count: 18267 \n",
      " Commercial Theft Count: 6618 \n",
      " Total Theft Count: 24885 \n",
      " Total Crime Count: 93164\n"
     ]
    }
   ],
   "source": [
    "res_thefts = clean[clean['res_theft'] == True]\n",
    "com_thefts = clean[clean['com_theft'] == True]\n",
    "print(\"Residential Theft Count: \" +  str(len(res_thefts)),\"\\n\",\n",
    "       \"Commercial Theft Count: \" + str(len(com_thefts)), \"\\n\", \n",
    "       \"Total Theft Count: \" + str(len(res_thefts)+ len(com_thefts)), \"\\n\",\n",
    "       \"Total Crime Count: \" +str(len(clean)))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "So that means about 27% of all the crimes in this dataset are either commercial or residential theft crimes. Around 73% of those burglaries are residential and 27% are commercial, which means people tend to steal from homes and individuals more often than stores or businesses. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Mean and Median of the Month Column\n",
    "\n",
    "To determine if crime occurrences tend to cluster toward the latter half of the year, we calculated the mean and median values for the month column.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "count    93164.000000\n",
      "mean         6.724003\n",
      "std          3.324811\n",
      "min          1.000000\n",
      "25%          4.000000\n",
      "50%          7.000000\n",
      "75%         10.000000\n",
      "max         12.000000\n",
      "Name: month, dtype: float64\n"
     ]
    }
   ],
   "source": [
    "month_stats = clean['month'].describe()\n",
    "\n",
    "print(month_stats)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The mean month value is 6.62, indicating that, on average, crimes tend to occur slightly more in the second half of the year.\n",
    "The median month value is 7, indicating that at least half of all reported crimes happened in July or later.\n",
    "The 25th percentile is at month 4 (April), and the 75th percentile is at month 9 (September), showing that most crimes are concentrated between these months.\n",
    "Since the maximum value is 12 and the distribution is fairly spread out, further investigation is necessary to determine whether December has a significantly higher rate of theft-related crimes than other months."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Mean and Median of Theft-Related Crimes\n",
    "\n",
    "Next, we want to see if theft-related crimes tend to cluster towards the latter half of the year as well."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "6.702304702468933 6.64233907524932\n"
     ]
    }
   ],
   "source": [
    "res_thefts_mean = res_thefts['month'].mean()\n",
    "com_thefts_mean = com_thefts['month'].mean()\n",
    "print(res_thefts_mean, com_thefts_mean)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Here we can see that both residential and commercial crimes have a mean above 6, which means that both of these crimes slightly tend towards that latter half of the year, which may indicate that residential and commercial thefts may occur more often in December, however since other months could also be affecting the mean here, this is data is not conclusive and we still need to do more research."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Residential Theft Count"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Now we will plot out the parts of the data to get a visual representation of the residential dataset pertaining to our research question."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0, 0.5, 'Theft Counts')"
      ]
     },
     "execution_count": 28,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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rVoVuW3//v1Yt25dp48/cuQIfvvb37b7XL/wwguQZTmyTdupBC+++CJKSkpgMpkwYcIE/Pjjj+1ei/A5oe1Q7LFD1if6TPYYRqLO5/Mxq9XKxo4dyxhj7B//+AcDwBYvXhzZ5p577mF6vZ45nc52j124cCEDwLZv384YY8zr9bJRo0axrKws9uKLL7Kvv/6avfLKK8xqtbLzzz+fybIceSwAVlBQwEaMGMHee+899s0337CdO3cyxhi76aab2KJFi9iqVavYqlWr2OOPP870ej2bP39+u+Nfd911TKFQsIceeoh99dVX7OWXX2aFhYXMarWyG2+8MbJdXV0dKywsZEVFRez//u//2Ndff80ef/xxptVq2U033XTS12jSpEls2LBhTJZlNmbMGNa/f38mCAJjjLGKigoGgD333HOR7f/yl7+wjt6ub775JgPAKioqIrcVFRWxPn36sOHDh7N//vOfbOXKlWz8+PFMrVazP//5z+zss89mn3zyCVu6dCkbNGgQs9lszOfzRR5/4403Mo1Gw/r27cuefPJJ9tVXX7F58+YxlUrFZs+e3e74//Ef/8HUajW777772BdffMHee+89NmTIEGaz2Zjdbm/3fDMyMlhhYSF79dVX2bfffsvWrl3b6evz7rvvMgBs+vTpbNmyZeyDDz5gY8aMYRqNhn3//feMMcbKy8vZX//6VwaAPfXUU2zDhg1s165dne7z22+/ZQDYv/71r3a3L1++nAFgL7zwQuS2Xbt2MavVysrKytjbb7/NvvrqK3bfffcxhULB5s2bF9luwYIFTKlUsr/85S9s9erV7IsvvmAvv/xyu206+huF/5633nor+/zzz9nf/vY3VlBQwHJzc9mkSZMi23X3/V9cXMzGjRvHPvzwQ7Zy5Uo2efJkplKp2MGDBxljjFVVVbG77rqLAWCffPIJ27BhA9uwYUPkczhp0qR2x2es65+djh57MgDYH//4xw7vC78PS0tL2fPPP8++/vpr9uc//5lxHNfu2JIksQsvvJAZjUY2f/58tmrVKvaPf/yDFRQUsKFDh0be2xs2bGAzZ85ker0+8rwPHz4c+fs8+uijkdurqqo6bXP4M9NVJ3rvH/uahT/7RUVF7OKLL2bLly9n77zzDrPZbGzQoEHshhtuYLfccgv7/PPP2euvv85MJhO7+OKL2x3vySefZBzHsVtu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991d+sIVz/PDsYxGI6655hq88cYbWLRoEaZNm3bcl4aw5ubmTs8rbdseduxzDK8U7M77PtqfyVNFq7Gi7I033gBjDB999BE++uij4+5/66238MQTT0CpVOK6667Dvffei8WLF+PJJ5/EkiVLcNlll7XrmcnKyoJer28XJLWVlZXV7veOJvG+//77UKvVWL58ebsT57Jly9ptF35T1tfXt+sVEUXxuA9BVlYWRowYgSeffLLDdoU/PF01atQoXHfddXjxxRcjF9S2wu3meb7d0txon8jDws+57QfVbrcD+PV1ysrKAsdx+P777ztcLnzsbV1dbRbef11d3XH31dbWQqFQdNh711X9+vWLTEo+77zzoNfr8eijj+LVV1/F/fffj/T0dCiVStxwww344x//2OE+SkpKAIRO+vfeey/uvfdeOBwOfP311/h//+//YcaMGaiqqupwNUn4+YVfz7bsdnskzwzQ/fd/tHX1sxNPWVlZyMzMxBdffNHh/W2/VUfDjBkz8Oqrr+LHH3/s8iqynlppGX4/fPTRR51e8MOKiooiC0n279+PDz/8EPPmzYMgCHj99ddP+Nh4nh86csstt+Af//gHtm/fjnfffbfT7TIzMzs9r4TbnKoo2IkiSZLw1ltvoX///vjHP/5x3P3Lly/HCy+8gM8//xyzZ89Geno6LrvsMrz99tuYMGEC7Hb7cTPoZ8+ejaeeegqZmZmRC0x3cRwHlUrVrjvS7/djyZIl7bY777zzAIRWMpxxxhmR2z/66KPjVljNnj0bK1euRP/+/U/rwtvWE088gY8++qjD5c/hC+D27dsjq0cA4LPPPovKsTvy7rvv4u677478/t577wFAZPXI7Nmz8fTTT6Ompua4ob/TMXjwYBQUFOC9997D/fffHzkJer1efPzxx5EVWtHywAMPYPHixXj66adx2223wWw2Y8qUKfjll18wYsSIyLfnk0lLS8NVV12FmpoazJ07F4cPH+5wafFZZ50FnU6Hd999F1deeWXk9vXr16OysrJdsBON9/+xuvPttKufnXiaPXs23n//fUiSdErpLbr7bf2ee+7BG2+8gTvuuOO4pedAaAXSsmXLcPnll3e7LadrxowZUKlUOHjwYLv31skMGjQIjz76KD7++GNs2bKlS4+J1/mhIxMmTMAtt9wCp9N5wtd96tSpWLBgAbZs2dLuHP/222+D4zhMmTKl28du+/5J1DQnAAU7UfX555+jtrYWzzzzTIdLgIcPH47XXnsNixYtwuzZswGEIvIPPvgAd955J/r06YNp06a1e8zcuXPx8ccf47zzzsM999yDESNGQJZlHDlyBF999RXuu+++k57gZs2ahRdffBHXX389/vM//xPNzc14/vnnj/tmMWzYMFx33XV44YUXoFQqcf7552PXrl144YUXYLVa242hP/bYY1i1ahUmTpyIu+++G4MHD0YgEMDhw4excuVKvP766+jTp0+3Xr+SkhLcfvvt7ZYth82cORMZGRm49dZb8dhjj0GlUmHx4sWoqqrq1jG6SqPR4IUXXoDH48HYsWOxfv16PPHEE7jooosiy73PPvts/Od//iduvvlmbNq0Ceeddx6MRiPq6uqwbt06lJWV4fbbb+/2sRUKBZ599ln85je/wezZs3HbbbeB53k899xzcDgcePrpp6P6XNVqNZ566inMmTMHr7zyCh599FG88sorOOecc3Duuefi9ttvR3FxMdxuN8rLy/HZZ59FxvYvvvhiDB8+HGeeeSays7NRWVmJl19+GUVFRZ0mKExPT8f999+PJ554Ar///e9x9dVXo6qqCvPmzTtuGCsa7/9jlZWVAQBeeeUV3HjjjVCr1Rg8eHCHPSBd/ezE07XXXot3330XM2fOxH/9139h3LhxUKvVqK6uxrfffotLL730hBfA/v37Q6/X491330VpaSlMJhPy8/M77Z0tKSnB+++/j2uuuQajRo2KJBUEgN27d0d6t+MR7BQXF+Oxxx7DI488gkOHDuHCCy9Eeno66uvr8fPPP8NoNGL+/PnYvn077rzzTlx99dUYOHAgNBoNvvnmG2zfvh0PPfTQSY8Tz/NDZ8K9VCdyzz334O2338asWbPw2GOPoaioCCtWrMDChQtx++23nzQhaUfCn6dnnnkGF110EZRKZbe+JPWYHp0OneIuu+wyptFoWENDQ6fbXHvttUylUkWWHUqSxAoLCxkA9sgjj3T4GI/Hwx599FE2ePBgptFoIkuC77nnnnbLF3GClR1vvPEGGzx4MNNqtaxfv35swYIFbNGiRcetSgkEAuzee+9lOTk5kVUXGzZsYFarld1zzz3t9tnY2MjuvvtuVlJSwtRqNcvIyGBjxoxhjzzyCPN4PCd8rdquxjp2nxaL5bjVWIyF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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "#get count\n",
    "theft_counts = clean.groupby([\"year\", \"month\"])[\"res_theft\"].sum().reset_index()\n",
    "theft_counts\n",
    "\n",
    "#plot\n",
    "sns.lineplot(data=theft_counts, x='month', y='res_theft')\n",
    "plt.xticks(range(1, 13), ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'])\n",
    "plt.title('Average Number of Residential Theft Crimes per Month')\n",
    "plt.xlabel('Month')\n",
    "plt.ylabel('Theft Counts')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "This line plot shows us the average number of residential theft crimes per month. We see some fluctuation throughout the year but theft gradually increases toward the end of the year and peaks in December. Since the count in December is noticeably higher compared to the averages of all other months, this strongly supports our hypothesis that December has a higher theft rate compared to the other months."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Commercial Theft Count"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Now we will look at the same type of graph on commercial theft to see if there are any noticeable differences compared to the residential graph."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0, 0.5, 'Theft Counts')"
      ]
     },
     "execution_count": 32,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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HQf27t2La665Bnq9HgkJCbj//vvh8Xhw+PBhTJs2DVqtFj179sQLL7zQ7PE7ejz9+OOPMXbsWOj1eqhUKvTu3bvd76zvdbr77rvx73//G7m5uZDL5cjLy8PKlSub3bYjx9C2XqO2iEQiLFiwACtWrIAgCP7t77zzDrKzs3HRRRe1eL/2jjvA7+/D/v37cf3110Ov1yM1NRW33HILjEZjk9fCarVixYoV/s/O2ccos9mMO+64A0lJSUhMTMRVV12F8vLyNp9b0DASdDabjen1ejZ69GjGGGP/+c9/GAC2fPly/23uu+8+plQqmdFobHLfN954gwFge/fuZYwxZrVa2bBhw1hSUhJ7+eWX2bfffsuWLl3K9Ho9mzJlChMEwX9fACwzM5Pl5+ez//3vf2zTpk3st99+Y4wxdtNNN7Fly5axjRs3so0bN7JnnnmGKZVKtmjRoiaPf/311zORSMQefvhhtmHDBvbKK6+w7Oxsptfr2Y033ui/XUVFBcvOzmY5OTns3//+N/v222/ZM888w+RyObvpppvafY0mTZrEBg0axARBYCNHjmR9+vRhLpeLMcZYcXExA8BefPFF/+2ffPJJ1tLH9d1332UAWHFxsX9bTk4Oy8rKYoMHD2YffvghW7duHRs7diyTSqXsiSeeYOeddx777LPP2OrVq1lubi5LTU1lNpvNf/8bb7yRyWQy1qNHD7Z48WK2YcMG9tRTTzGJRMJmzJjR5PFvu+02JpVK2QMPPMDWr1/P/ve//7EBAwaw1NRUVllZ2eT5JiQksOzsbPbaa6+xzZs3s61bt7b6+nzwwQcMALvkkkvY559/zlatWsVGjhzJZDIZ+/777xljjB07doz985//ZADYc889xwoLC9n+/ftb3afvuXbUc889xwCw66+/nq1du5a99957rHfv3kyv17MjR440e70GDhzIli5dyjZu3MhuvvlmBoA98sgjLDc3ly1btox98803bMaMGQwA27lzp//+vvewV69e7IEHHmAbNmxgzz//PBOLxez6669nI0aMYM8++yzbuHEje+ihhxgA9tJLL/nvz/M8mzZtGlOr1WzRokVs48aN7D//+Q/LzMxkeXl5Td7bnJwclp6eznr37s3eeecdtnnzZvbLL7+wU6dOsfT09Cbfs1WrVrFbbrmFHTx4kDH2++fy3Xff9e9v69at7IEHHmCffPIJ27p1K1u9ejW78sormVKpZIcOHfLfrqX7tsf3uuzYsaPF6wGwnj17sjFjxrCPPvqIrVu3jk2ePJlJJBJ2/Phx/+3279/P9Ho9GzJkCHvvvffYhg0b2AMPPMBEIhF76qmnGGOMVVdXs8LCQgaAzZkzhxUWFrLCwkJ27NgxNmfOHAbAv62wsJA5HI4W2/TTTz8xAOyhhx7q0HP0vS6ZmZnswgsvZJ988gnbsGEDKy4ubvE18x0H+vfvz5555hm2ceNG9uCDDzIA7O6772YDBgxgr776apPP4Keffuq/f0ePpz/99BPjOI5dd911bN26dWzTpk3s3XffZfPnz2/3OQFg2dnZLC8vj3344YdszZo1bNq0aQwA+/jjj/236+gxtK3XqDU5OTns8ssvZ8eOHWMcx7F169YxxhjzeDwsMzOTPfHEE+zjjz9mANjmzZv99+vIcefs9+GJJ55gGzduZC+//DKTy+Xs5ptv9t+usLCQKZVKdtlll/k/O75jlO/z3bt3b/aXv/yFffPNN+w///kPi4+PZxdeeGG7r3MwUADUBd577z0GgP3rX/9ijDFmNpuZRqNhF1xwgf82e/fuZQDYW2+91eS+Y8aMYSNHjvT/XVBQwEQiUbOD4CeffMIA+D/YjHm/eHq9ntXX17fZPp7nmdvtZk8//TRLTEz0f+n379/f4sHrww8/ZACaBEB/+tOfmEajYSdPnmxy27///e8MQJs/xIz9HgAxxti3337LALDXXnuNMRacAEipVLJTp075txUVFTEALD09nVmtVv/2zz//nAFga9as8W+78cYbGQC2dOnSJo+1ePFiBoD98MMPjDHm/8Fo/GPMGGNlZWVMqVSyBx98sMnzBcC+++67Nl8XxrzvT0ZGBhsyZAjjed6/3Ww2s5SUFDZhwgT/ts2bNzc7sLZGoVCwcePGtXs7xhhraGjwH7gaKy0tZXK5nM2bN8+/zfd6Nf6hcbvdLDk5mQFgu3fv9m+vq6tjYrGY3X///f5tvvfwL3/5S5PHuvLKKxkA9vLLLzfZPmzYMDZixAj/377PZ+PHZ4yxHTt2MADsjTfe8G/LyclhYrGYHT58uMltb7nlFiaVStmBAwdafU06EsR4PB7mcrlYv3792H333RfQfc/WkQAoNTWVmUwm/7bKykomEolYQUGBf9ull17KsrKymp1s3X333UyhUDQ5XgBgd911V5Pb3XXXXS1+91qycuXKJse+9vhel8YnQGdf11IAdPZ3btiwYQwA++yzz/zbfJ/Bq666yr+to8dT33HMYDB06Hk0BoAplcomJ0Aej4cNGDCA9e3b17+to8fQtl6j1vgCIMa8x545c+Ywxhhbu3Yt4ziOFRcXNwuAAjnu+N6HF154ocnj3nnnnUyhUDQ5MVer1U1+O3x8n+8777yzyfYXXniBAWAVFRUdeq7ngobAusCyZcugVCpx3XXXAQA0Gg2uueYafP/99zh69CgAYMiQIRg5ciTeffdd//0OHjyIX375pUk361dffYXBgwdj2LBh8Hg8/sull17aYgb/lClTEB8f36xNmzZtwkUXXQS9Xg+xWAypVIonnngCdXV1qK6uBgBs3boVAHDttdc2ue+cOXMgkTRNF/vqq69w4YUXIiMjo0m7fLkDvn11xNSpU3HJJZfg6aefhtls7vD92jJs2DBkZmb6/x44cCAA71BU47wb3/aTJ08228cNN9zQ5O958+YBgL/r+auvvgLHcfjDH/7Q5DVIS0vD0KFDm7038fHxHUr2Pnz4MMrLyzF//nyIRL9/RTUaDa6++mps37692VBcsBUWFsJutzcb9szOzsaUKVPw3XffNdnOcRwuu+wy/98SiQR9+/ZFeno6hg8f7t+ekJCAlJSUFl/vGTNmNPnb995cfvnlzbY3vv9XX32FuLg4zJw5s8n7MGzYMKSlpTV7H/Lz85slin/99de48MIL/Y/ZUR6PB8899xzy8vIgk8kgkUggk8lw9OjRZkOFXeHCCy+EVqv1/52amtrk9XU4HPjuu+8we/ZsqFSqJq/PZZddBofDge3bt3d5O9tzxRVXQCqVdvj2LX1WOI5rkrvk+wye/VnpyPF09OjRALzHwo8++ijg2ZFTp05Famqq/2+xWIy5c+fi2LFjOHXqlL8tgRxDA32NfG655RasWbMGdXV1WLZsGS688EL07Nmz2e06c9y54oormvydn58Ph8Ph/03piJb2AbR8TA42CoCC7NixY9i2bRsuv/xyMMZgMBhgMBgwZ84cAL/PDAO8H8zCwkJ/suO7774LuVyO66+/3n+bqqoq7N27F1KptMlFq9WCMYba2tomj5+ent6sTb/88gsuueQSAMDbb7+NH3/8ETt27MBjjz0GwJsECgB1dXUA0OSLC3gPJImJiU22VVVV4csvv2zWrkGDBgFAs3a15/nnn0dtbW3Qpr4nJCQ0+Vsmk7W53eFwNNne0nNOS0sD8PvrVFVVBcYYUlNTm70O27dv79B70xLf/lu6fUZGBgRBQENDQ4f21ViPHj1QXFwclDb4rvdRqVRQKBRNtvmmPp9NJpM1e72BwN6zxvevqqqCwWCATCZr9j5UVlZ26H2oqanp1Oyq+++/H48//jiuvPJKfPnll/j555+xY8cODB061P+96kpnf0YBb7J24++0x+PBa6+91uy18QWsgX5X29KjRw8A6PDnzKej3w2flj4TrX0Gz/6sdOR4OnHiRHz++efweDxYsGABsrKyMHjwYHz44Ycdap/vWNHStsbHj0COoYG+Rj5z5syBQqHAP/7xD3z55Ze49dZbW7xdZ447Z3/+fEnZgXz2g7GPzqJZYEH2zjvvgDGGTz75BJ988kmz61esWIFnn30WYrEY119/Pe6//34sX74cixcvxn//+19ceeWVTXpwkpKSoFQqmwROjSUlJTX5u6VE4ZUrV0IqleKrr75qcoA4e20G3wexqqqqSe+Jx+Np9oOXlJSE/Pz8JrMLGsvIyGhxe2uGDRuG66+/Hi+//HKTngQfX7udTmeTmQ/BPHg35nvOjb+clZWVAH5/nZKSksBxHL7//vsWZ2Ocva2js9x8+6+oqGh2XXl5OUQiUYu9fO259NJL8dprr2H79u3tzq5prw1nf+5CyZc8uX79+havb9xDArT8PiQnJ/vPzAPx/vvvY8GCBXjuueeabK+trUVcXFzA+wu2+Ph4iMVizJ8/H3fddVeLt+nVq1fQHm/UqFFISEjAF198gYKCgg5/5rtrBmggx9NZs2Zh1qxZcDqd2L59OwoKCjBv3jz07NkT48ePb/NxfMeKlrY1Pn4Ecgzt7GukUqlw3XXXoaCgADqdrtlEB5+uOu6EMwqAgojneaxYsQJ9+vTBf/7zn2bXf/XVV3jppZfw9ddfY8aMGYiPj8eVV16J9957D+PHj0dlZWWzWQYzZszAc889h8TExE4fqDiOg0QigVgs9m+z2+3473//2+R2EydOBOBdWG/EiBH+7Z988kmzmV0zZszAunXr0KdPn6B9KZ599ll88skn/lk5jfm6bPfu3evvnga8i611lQ8++AD33HOP/+///e9/AOCfxTBjxgwsWbIEp0+fbjZseC769++PzMxM/O9//8Nf//pX/4HParXi008/9c/QCNR9992Hd955B3feeWezafCAd0bb559/jtmzZ2P8+PFQKpV4//33cc011/hvc+rUKWzatMnfoxkOZsyYgZUrV4Ln+U4vNTF9+nT897//xeHDh9G/f/8O34/juGaB7tq1a3H69Gn07du3U20JJpVKhQsvvBB79uxBfn6+v1ctEI3PyNtbLkAqleKhhx7CQw89hGeeeabZNHgAqK6uxtGjR3HeeecF3JZz1ZnjqVwux6RJkxAXF4dvvvkGe/bsaTcA+u6771BVVeXvTed5HqtWrUKfPn38PY1dcQxtzR133IGqqipMmjSpWS+ZT1cddxr3SIYbCoCC6Ouvv0Z5eTmef/75FqcjDx48GK+//jqWLVvmH8O+5ZZbsGrVKtx9993IyspqNjVx4cKF+PTTTzFx4kTcd999yM/PhyAIKC0txYYNG/DAAw+0e9C//PLL8fLLL2PevHm4/fbbUVdXh7///e/NDtyDBg3C9ddfj5deeglisRhTpkzB/v378dJLL0Gv1zcZF3766aexceNGTJgwAffccw/69+8Ph8OBkpISrFu3Dv/6178CHlLo1asX7rjjDixdurTZdZdddhkSEhJw66234umnn4ZEIsHy5ctRVlYW0GN0lEwmw0svvQSLxYLRo0fjp59+wrPPPovp06f7p/Ced955uP3223HzzTdj586dmDhxItRqNSoqKvDDDz9gyJAhuOOOOwJ+bJFIhBdeeAE33HADZsyYgT/96U9wOp148cUXYTAY/NPLA9WrVy+sXLkSc+fOxbBhw/wLIQLAgQMH/L2Xs2fPRlxcHB5//HE8+uijWLBgAa6//nrU1dVh0aJFUCgUePLJJzvVhq5w3XXX4YMPPsBll12Ge++9F2PGjIFUKsWpU6ewefNmzJo1C7Nnz25zH08//TS+/vprTJw4EY8++iiGDBkCg8GA9evX4/7772+yEGFjM2bMwPLlyzFgwADk5+dj165dePHFF7t0scJALV26FOeffz4uuOAC3HHHHejZsyfMZjOOHTuGL7/8Eps2bWrz/kOGDAHgHaaePn06xGJxm8HU//3f/+HgwYN48skn8csvv2DevHn+hRC3bduGt956C4sWLQpJANTR4+kTTzyBU6dOYerUqcjKyoLBYMDSpUshlUrbXW8L8PbuTJkyBY8//jjU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VqxoELcncWe8zTkODxw4ALVajWXLlmHBggU4fPiw01NiALBgwQI88MADiI+PR0JCArZv347jx4+je/fuosV68eJF3HvvvUhLS0N0dDS0Wi2OHj2Kp556CmPGjMHw4cMxcOBAjB07FuvXr0dkZCTOnz+PDz74AGPHjhWqsZVKJWbMmIFnnnkGFRUVWLhwISZOnAiDwSBKnC+++CISEhKQnJyMNWvWoFu3bjh58iQWLVqELl26YO3atfD398eMGTOQlpaGjRs3IiYmBj/99BMuXLiAiRMnIjw8HBzH4f3338eoUaOgUqmg0WhEie9qt9xyC1JTU51uSh577DH07dsX//jHPzBp0iR8+eWXePHFF/HSSy85LZuamor09HRYLBbheiUWs9mM0tJS2O12/Prrr9i3bx8yMjKQkpKC6dOnQyKRXPf7XrlyJYYNG4YePXrgvvvug81mw969e7F48WJRY6VG0CKaNm0amzBhAmOMsf3797PevXsznudZdHQ0y8/Pd2pkV9dI99tvvxWWLysrYwDYp59+6pL4rtVAbd++fSwhIYGpVCqm0+lYv3792KuvvipMB8A2bdrEkpKSGM/zLDw8nOXk5Nyw+BhjTg14W7N/xZCSksJGjRrV6LSCggIGgG3YsIEBYO+99x67+eabmUKhYH379nVq8NxYA1UxiLkP61RWVjK1Ws3mzp0rerz1z5ny8nI2ceJEptPpmNFoZNnZ2c1qVKzX61lWVpbosbkqXjE05zgsKChg7777LouIiGBKpZKlpKSwV199lV192V+9ejULDAxkGo2GpaWlsYULF7IBAwaIFqvJZGJLlixhcXFxTK/XM7VazSIjI9njjz/OampqGGOMVVRUsAULFrCQkBAml8uZ0Whkqamp7OzZs4yxK42gY2Ji2EsvvcRCQkKYUqlk48ePZ5cuXRItTsYYKy4uZjNnzmQGg0GIY8GCBez3338X5qmtrWWPPPIICw4OZgqFgkVERLDMzExh+urVq5nBYGAcxzX5wEFrNHZuFxcXM57nnb7Td955h0VFRTG5XM7CwsLY008/3WBdZWVljOd5plarWWVlpagxAmAAmEwmY506dWLDhw9nmZmZzG63C/Nd7/tmjLEdO3aw2NhYplAoWGBgIBs/frxocdbhGHNRha8XGjFiBCIiIvDiiy+6OxTiRvn5+UhMTERZWdk12zC0F+fOnUPXrl1x5MgRxMXFibru9nbOtLd4WyMpKQkGgwFvvPGGu0MRpKenY+fOnQ2q8AhpC6oCE0FZWRkOHTqE/Pz8RrsgIKQ9slqtKCkpwZIlSzBgwABRk5/2ds60t3ibq6amBq+88gqSk5MhlUqRk5ODjz/+GPv373d3aIS4HCVAIkhLS8ORI0fw2GOPYcyYMe4OhxBRfPHFF0hMTESvXr3wzjvviLru9nbOtLd4m4vjOHzwwQdYs2YNzGYzIiMjsWPHjkYb+BLS0VAVGCGEEEK8Dr0IkRBCCCFehxIgQgghhHgdSoAIIYQQ4nUoASKEEEKI16EEiBBCmonjOOzcudPdYRBCREAJECHE482cORMcxzX6Dp65c+eC4zhRe6lPT09HbGysaOsjhHgeSoAIIe2C0WhEbm4uamtrhXEmkwk5OTlCp7OEENJclAARQtqFuLg4hIWFIS8vTxiXl5cHo9GIW2+9VRhnNpuxcOFCBAUFQalUYvDgwThy5IgwPT8/HxzH4cCBA4iPj4darUZCQgJOnz4NAMjOzsaqVatw7NgxcBwHjuOcOhH9/fffMW7cOKjVavTs2RO7d+92/cYTQkRHCRAhpN24//77kZWVJQxnZmYiLS3NaZ7Fixdjx44d2Lp1K7755htEREQgOTkZly5dcppv+fLl2LBhA44ePQqZTCasZ9KkSXjsscdw8803o6SkBCUlJZg0aZKw3KpVqzBx4kQcP34co0aNQmpqaoN1E0I8HyVAhJB2Y9q0aTh48CCKi4vx008/4YsvvsDUqVOF6dXV1Xj55Zfx9NNPY+TIkYiKisJrr70GlUqFLVu2OK1r7dq1uOOOOxAVFYUlS5bg0KFDMJlMUKlU0Gg0kMlkMBgMMBgMUKlUwnIzZ87E5MmTERERgXXr1qG6uhqHDx++YfuAECIO6guMENJuBAYGYvTo0di6dSsYYxg9ejQCAwOF6T/++COsVisGDRokjJPL5ejXrx+Kioqc1hUdHS38HRwcDAC4cOHCddsT1V/Ox8cHWq0WFy5caNN2EUJuPEqACCHtSlpaGubPnw8A2LRpk9O0uq4NOY5rMP7qcXK5XPi7bprD4bju/6+/XN2yzVmOEOJZqAqMENKujBgxAhaLBRaLBcnJyU7TIiIioFAocPDgQWGc1WrF0aNH0bt372b/D4VCAbvdLlrMhBDPQyVAhJB2RSqVCtVZUqnUaZqPjw/mzJmDRYsWwd/fH2FhYXjqqadQU1ODWbNmNft/dO3aFWfOnEFhYSFCQ0Oh1WrB87yo20EIcS9KgAgh7Y5Op2ty2pNPPgmHw4Fp06ahsrIS8fHx+PDDD+Hn59fs9U+YMAF5eXlITEzE5cuXkZWVJeqLFgkh7sexukpzQgghhBAvQW2ACCGEEOJ1KAEihBBCiNehBIgQQgghXocSIEIIIYR4HUqACCGEEOJ1KAEihBBCiNehBIgQQgghXocSIEIIIYR4HUqACCGEEOJ1KAEihBBCiNehBIgQQgghXocSIEIIIYR4nf8H6X3UoCXERcYAAAAASUVORK5CYII=",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "#get count\n",
    "theft_counts = clean.groupby([\"year\", \"month\"])[\"com_theft\"].sum().reset_index()\n",
    "theft_counts\n",
    "\n",
    "#plot\n",
    "sns.lineplot(data=theft_counts, x='month', y='com_theft')\n",
    "plt.xticks(range(1, 13), ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'])\n",
    "plt.title('Average Number of Commercial Theft Crimes per Month')\n",
    "plt.xlabel('Month')\n",
    "plt.ylabel('Theft Counts')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "This line plot shows the average number of commercial thefts per month. This lineplot is a lot more volatile compared to the previous residential graph however we do see a gradual increase toward the end of the year as well. The average count for December is only rivaled by the average count in August. This still supports our hypothesis since December has a higher average count than most of the other months, but not as much as the residential count."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Residential Theft Proportion"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Since the average counts of residential and commercial thefts do not take into consideration the total number of crimes that occurred that month, it may not be completely accurate in representing the theft crime rate of that month. To address this, we will graph the proportion of residential theft to give a more accurate view of the theft rate."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 36,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0, 0.5, 'Theft Proportion')"
      ]
     },
     "execution_count": 36,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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WCBmz54tatWqJWQymWjWrJnYu3dvqeXHjBkjatasKaysrISbm5to166d+OSTT0pch7K+n0qj+o58ktKGwQshxIoVK0STJk2ETCYTjo6Ool+/furRcSplvQ6q9+yjDhw4IJo1aybkcrkAoP5caPOZrG4kQghRVckWVS8SiQQTJ07Ed999Z+hQiIjUbt68CX9/f3z++ef43//+Z+hwyEixDxARERGZHSZAREREZHbYBEZERERmhzVAREREZHaYABEREZHZYQJEREREZocTIZZCqVTi3r17sLe3r7Kp4YmIiKhyhBDIyMiAt7c3LCyeXMfDBKgU9+7dK7FyOREREZmG27dvq5djKgsToFKo1uS5fft2idXSiYiIyDilp6fDx8fnqWvrAUyASqVq9nJwcGACREREZGLK032FnaCJiIjI7DABIiIiIrPDBIiIiIjMDhMgIiIiMjtMgIiIiMjsMAEiIiIis8MEiIiIiMwOEyAiIiIyO0yAiIiIyOwwASIiIiKzwwSIiIiIzA4TICIiIjI7TICIiIioyuTkFyHmXjryC5UGjYMJEBEREVWZqNsP0eubP9F94RGDxsEEiIiIiKpMTHw6AKCuu51B42ACRERERFUm5l5xAtTQ28GgcTABIiIioiqjqgFq6MUEiIiIiMxAfqESVxMzAADBNR0NGgsTICIiIqoSVxIzUFAk4GhtBW9HhUFjYQJEREREVULd/8fLARKJxKCxMAEiIiKiKqHu/2PgDtAAEyAiIiKqIo/WABkaEyAiIiLSOyEEa4CIiIjIvNxJzUFGbiFkUgsEuBl2EkSACRARERFVgeh/m7/qethBZmn49MPwERAREVG1ZywTIKowASIiIiK9M5YlMFSYABEREZHexbIGiIiIiMzJw+x83H2YAwBowBogIiIiMgeq/j+1XWzgoLAycDTFmAARERGRXhnTBIgqTICIiIhIr4xpAkQVJkBERESkV6wBIiIiIrOSV1iEq4mZAFgDRERERGbiyv1MFCoFnGys4OWoMHQ4akyAiIiISG8ebf6SSCQGjuY/TICIiIhIb4xtCQwVJkBERESkN8a2BIYKEyAiIiLSC6VSGOUQeIAJEBEREenJndQcZOYVQmZpgQA3O0OHo4EJEBEREelFTHwaACDIwx5WUuNKOYwrGiIiIqo2jHECRBWDJ0CLFy+Gv78/FAoFWrRogT//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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "\n",
    "#Get crime and total counts\n",
    "crime_count = clean.groupby('month').size()\n",
    "res_theft_count = clean[clean['res_theft']].groupby('month').size()\n",
    "\n",
    "#Compute proportion\n",
    "res_theft_prop = (res_theft_count / crime_count).reset_index()\n",
    "res_theft_prop.columns = ['Month', 'TheftProportion']\n",
    "\n",
    "#plot\n",
    "sns.lineplot(data=res_theft_prop, x='Month', y='TheftProportion')\n",
    "plt.xticks(range(1,13), ['Jan','Feb','Mar','Apr','May','June','July','Aug','Sept','Oct','Nov','Dec'])\n",
    "plt.title('Proportion of Residential Theft Crimes per Month')\n",
    "plt.xlabel('Month')\n",
    "plt.ylabel('Theft Proportion')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "This line plot highlights the proportion of residential theft relative to total thefts per month. During December we see a significant spike in residential theft further starting around October proving that December is a key month for residential theft. This strongly supports our hypothesis since the proportion of residential theft crime is way higher than every other month except for January, which is right after December. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Commercial Theft Proportion"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 39,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0, 0.5, 'Theft Proportion')"
      ]
     },
     "execution_count": 39,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "#Get crime and total counts\n",
    "crime_count = clean.groupby('month').size()\n",
    "com_theft_count = clean[clean['com_theft']].groupby('month').size()\n",
    "\n",
    "#Compute proportion\n",
    "com_theft_prop = (com_theft_count / crime_count).reset_index()\n",
    "com_theft_prop.columns = ['Month', 'TheftProportion']\n",
    "\n",
    "#plot\n",
    "sns.lineplot(data=com_theft_prop, x='Month', y='TheftProportion')\n",
    "plt.xticks(range(1,13), ['Jan','Feb','Mar','Apr','May','June','July','Aug','Sept','Oct','Nov','Dec'])\n",
    "plt.title('Proportion of Commercial Theft Crimes per Month')\n",
    "plt.xlabel('Month')\n",
    "plt.ylabel('Theft Proportion')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "This line plot highlights the proportion of commercial theft relative to total thefts per month. During December we also see a significant spike in commercial theft starting in September further proving that December is a key month for commercial theft as well as theft as a whole. This still supports our hypothesis since the theft proportion in December is still higher than most other months."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Percentage Change in Proportion of Residential Theft"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Finally, to answer our research question, we will look at the percent change of December's residential theft proportion relative to every other month."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 43,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Month</th>\n",
       "      <th>TheftProportion</th>\n",
       "      <th>percent change</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>1</td>\n",
       "      <td>0.223968</td>\n",
       "      <td>5.129417</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>2</td>\n",
       "      <td>0.202562</td>\n",
       "      <td>16.238688</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>3</td>\n",
       "      <td>0.208525</td>\n",
       "      <td>12.915131</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>4</td>\n",
       "      <td>0.200654</td>\n",
       "      <td>17.344427</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>5</td>\n",
       "      <td>0.181371</td>\n",
       "      <td>29.819802</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>6</td>\n",
       "      <td>0.182472</td>\n",
       "      <td>29.036541</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>6</th>\n",
       "      <td>7</td>\n",
       "      <td>0.178107</td>\n",
       "      <td>32.199003</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>7</th>\n",
       "      <td>8</td>\n",
       "      <td>0.185260</td>\n",
       "      <td>27.094794</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>8</th>\n",
       "      <td>9</td>\n",
       "      <td>0.185530</td>\n",
       "      <td>26.909832</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9</th>\n",
       "      <td>10</td>\n",
       "      <td>0.187719</td>\n",
       "      <td>25.429790</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>10</th>\n",
       "      <td>11</td>\n",
       "      <td>0.198211</td>\n",
       "      <td>18.790624</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "    Month  TheftProportion  percent change\n",
       "0       1         0.223968        5.129417\n",
       "1       2         0.202562       16.238688\n",
       "2       3         0.208525       12.915131\n",
       "3       4         0.200654       17.344427\n",
       "4       5         0.181371       29.819802\n",
       "5       6         0.182472       29.036541\n",
       "6       7         0.178107       32.199003\n",
       "7       8         0.185260       27.094794\n",
       "8       9         0.185530       26.909832\n",
       "9      10         0.187719       25.429790\n",
       "10     11         0.198211       18.790624"
      ]
     },
     "execution_count": 43,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#code\n",
    "res_dec_prop = res_theft_prop.loc[res_theft_prop['Month'] == 12, 'TheftProportion'].values[0]\n",
    "res_theft_prop['percent change'] = ((res_dec_prop / res_theft_prop['TheftProportion']) - 1) * 100\n",
    "res_theft_prop_clean = res_theft_prop[res_theft_prop['Month'] != 12]\n",
    "res_theft_prop_clean\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The percent change column represents how much larger or smaller the residential theft proportion is in December relative to each month. For example, the rate of residential theft in December is approximately 5% higher relative to January (month 1) and about 32% higher relative to July (month 7). Looking at the whole column, we can see that December has a higher rate of residential theft compared to every other month in the year."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 45,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "21.90073179610553"
      ]
     },
     "execution_count": 45,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "res_theft_prop_clean['percent change'].mean()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Looking at the mean of the percent change column allows us to see that December had a significantly higher rate of residential theft, around 22%, when compared to each of the other months in the year. This means that the proportion of residential theft in December is approximately 19% higher relative to the average proportion of residential theft crimes in all the other months. This is a strong indicator that the rate of residential theft is higher in December compared to the rest of the year."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Percentage Change in Proportion of Commercial Theft"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Now we do the same thing for commercial theft proportion."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 49,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Month</th>\n",
       "      <th>TheftProportion</th>\n",
       "      <th>percent change</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>1</td>\n",
       "      <td>0.075703</td>\n",
       "      <td>10.094191</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>2</td>\n",
       "      <td>0.079630</td>\n",
       "      <td>4.664766</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>3</td>\n",
       "      <td>0.082233</td>\n",
       "      <td>1.351924</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>4</td>\n",
       "      <td>0.075032</td>\n",
       "      <td>11.079038</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>5</td>\n",
       "      <td>0.065004</td>\n",
       "      <td>28.215489</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>6</td>\n",
       "      <td>0.064992</td>\n",
       "      <td>28.239050</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>6</th>\n",
       "      <td>7</td>\n",
       "      <td>0.069555</td>\n",
       "      <td>19.825221</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>7</th>\n",
       "      <td>8</td>\n",
       "      <td>0.064824</td>\n",
       "      <td>28.570540</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>8</th>\n",
       "      <td>9</td>\n",
       "      <td>0.060888</td>\n",
       "      <td>36.881568</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9</th>\n",
       "      <td>10</td>\n",
       "      <td>0.066199</td>\n",
       "      <td>25.900705</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>10</th>\n",
       "      <td>11</td>\n",
       "      <td>0.072971</td>\n",
       "      <td>14.215940</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "    Month  TheftProportion  percent change\n",
       "0       1         0.075703       10.094191\n",
       "1       2         0.079630        4.664766\n",
       "2       3         0.082233        1.351924\n",
       "3       4         0.075032       11.079038\n",
       "4       5         0.065004       28.215489\n",
       "5       6         0.064992       28.239050\n",
       "6       7         0.069555       19.825221\n",
       "7       8         0.064824       28.570540\n",
       "8       9         0.060888       36.881568\n",
       "9      10         0.066199       25.900705\n",
       "10     11         0.072971       14.215940"
      ]
     },
     "execution_count": 49,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#code\n",
    "com_dec_prop = com_theft_prop.loc[com_theft_prop['Month'] == 12, 'TheftProportion'].values[0]\n",
    "com_theft_prop['percent change'] = ((com_dec_prop / com_theft_prop['TheftProportion']) - 1) * 100\n",
    "com_theft_prop_clean = com_theft_prop[com_theft_prop['Month'] != 12]\n",
    "com_theft_prop_clean"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The percent change column represents how much larger or smaller the commercial theft proportion is in December relative to each month. For example, the rate of commercial theft in December is approximately 10% higher relative to January (month 1) and about 20% higher relative to July (month 7). Looking at the whole column, we can see that December has a higher rate of commercial theft compared to every other month in the year."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 51,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "19.00349383694285"
      ]
     },
     "execution_count": 51,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "com_theft_prop_clean['percent change'].mean()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Looking at the mean of the percent change column allows us to see that December had a significantly higher rate of commercial theft as well, around 19%, when compared to each of the other months in the year. This means that the proportion of commercial theft in December is approximately 19% higher relative to the average proportion of commercial theft crimes in all the other months. This is a strong indicator that the rate of commercial theft is higher in December compared to the rest of the year."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Ethics & Privacy"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Our research question pertains to crimes and as such contains personal or private information about the victims, however, the data we are using for our research question only involves the date of the crime and the type of crime committed. This means that there is no personal information involved in our project and all the data we are using for our project is public information, so there are no privacy or terms of use concerns. Our dataset could have a potential bias since it only looks at the crime in the City of Cambridge, which could skew the data and may not represent the rest of the world, however, our research question specifically concerns Cambridge so this won't be an issue. We will also be transparent about where the data comes from and what locations the dataset is about. Data about crime can often be used to misrepresent and affect marginalized groups, but our project will not utilize data pertaining to ethnicity or gender so this will not be an issue. \n",
    "Another potential issue would be the time frame in which the data was collected, since our dataset has data from 2020 and 2021, it will likely be affected by the COVID-19 pandemic, which may affect the data in a way that it wouldn't accurately represent a typical year of crime in Cambridge. This will not be too big of an issue for our dataset since it spans from 2009 to 2024, meaning we have plenty of other years to look at and compare. Since our dataset only handles reported crimes, then it may not truly represent all crimes in Cambridge, since not all crimes are reported, and certain crimes like shoplifting may be easier to get away with without getting reported compared to other crimes like homicide. One last concern with utilizing reported crimes as data could be that the time at which a crime is reported, will likely not perfectly match up with when the crime actually occurred, which may slightly skew the data, however since our research question is looking over a month-long period of time, this will not make a significant difference to our data since the time between a report and when the crime occurred is generally within a month-long period."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Discusison and Conclusion\n",
    "\n",
    "\n",
    "Our exploratory data analysis of theft-related crimes in the city of Cambridge between 2009 and 2023 sought to determine whether theft-related crimes spiked in December when compared to other months. The EDA that we performed has been able to provide valuable insights into crime trends, patterns, and other potential influencing factors. Given the common belief that burglary rates increase during the holiday season, we looked into theft trends to determine whether December stood out when compared to other months. We examined theft across all months and compared theft rates in December. \n",
    "\n",
    "The results we saw indicate that the proportion of commercial and residential thefts spiked in December. This aligns directly with our hypothesis since during this month there are usually a lot more valuable items in people's homes as well as stores. These findings suggest that while December may not have the most overall crime, a large percentage of crime in December is theft-related specifically residential and commercial theft. \n",
    "\n",
    "During December, people tend to travel a lot more during this time leaving their homes unoccupied which can also lead to more residential theft. As for commercial theft, there is usually an increase in consumer spending and crowds in shopping areas which can also contribute to more commercial theft. Stores usually have more inventory during this time which can lead to more cases of theft during this time. Even though the total amount of commercial theft is not the highest, its proportion relative to total crime is significantly higher making theft an overall dominant type of crime in December.\n",
    "\n",
    "Throughout the year the average number of residential crimes gradually increases and peaks in December. We also see a similar trend with commercial crime. There is a gradual increase as well but commercial crime doesn’t peak in December. But there is still a significant spike in the proportion graph for December. \n",
    "\n",
    "Overall when looking at our analysis, it is apparent that December has the highest proportion of residential and commercial thefts compared to other months of the year. Residential thefts most likely spike in December due to an increased amount of valuables in people's homes and holiday travel. Commercial theft also ties in with residential theft since there is an increased amount of consumer spending and shopping activity which leads to more valuables in homes thanks to this extra spending. Although the average number of residential and commercial crimes in December isn't significantly higher when compared to other months with higher average theft, the proportion of theft is significantly higher than in other months which makes December a key month for commercial and residential theft. With this analysis, we were able to confirm our hypothesis since the rate of theft crimes was over 10% higher in December when compared to the average of other months. \n",
    "\n",
    "\n",
    "\n",
    "\n",
    "\n",
    "# Team Contributions\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "\n",
    "- Vincent Luu: For the project proposal: worked on the research question, background, hypothesis, found the data, and ethics. For the DataCheckpoint: fixed and edited the research question, background, hypothesis, ethics, found new data, and wrangled/cleaned data. For the EDACheckpoint, added variables to data portion, came up with EDA ideas, did proportion graphs, fixed minor errors and added some explanation. For the final project, worked on the abstract, created new columns redefining residential and commercial theft, reorganized and formatted EDA and organized tasks for the group, added some new explantions for EDA, added background section in slides for presentation.\n",
    "\n",
    "- Srikar Mannam: Brainstormed ideas and research questions for the project, wrote the conclusion, created slides for the conclusion, recorded a segment of the video for the conclusion, helped create explanations for the graphs, minor fixes and adjustments to the entire notebook, and performed a portion of the EDA consisting of total number of thefts as well as percent change.\n",
    "\n",
    "- Jayminn Anand: Brainstormed ideas, created EDA columns and added explanations, worked on the slides for the presentation (data/visual slides), recorded part of the video for the presentation, fixed minor errors.\n",
    "\n",
    "- Angela Perez: Brainstormed research questions, worked on EDA visuals, started presentation slides (worked on research question, hypothesis, and visuals slides), recorded visual portion of the team video, and proofread and made minor adjustments to overall project.\n",
    "\n",
    "- Slater Mutunga: Brainstormed for the research question, calculated, graphed, and analyzed the mean and median of thefts by month, recorded portion for the team video, edited together the team video, proofread final project, and fixed minor errors."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python [conda env:base] *",
   "language": "python",
   "name": "conda-base-py"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.12.7"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
