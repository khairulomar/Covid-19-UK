# Analysis of Covid-19 in the UK
<b>Updated as of 22 Feb 2021</b>

### Objective
Since the onset of the pandemic, multiple public and private organizations in the UK have published various methods and formats of data analysis to track the spread and severity of Covid-19 using government figures released via an <a href="https://coronavirus.data.gov.uk/">API</a>, for which this repository is based on. Despite the multitude of data visualisations that are published daily by the government and media outlets, <b>I have yet to come across several formats that I believe would be even more useful in understanding the latest situation and trend. My analysis in this repository aims to showcase these new visualization ideas</b>.
<p>
Charts below are best viewed on a widescreen format: click each chart to expand to full-sized resolution. For details on Python codes used to derive these visualizations, refer to the <a href="https://nbviewer.jupyter.org/github/khairulomar/Covid-19-UK/blob/main/uk-covid.ipynb?flush_cache=true">Jupyter notebook</a>.

### All-in-one view by region
The first chart is inspired by the <a href="https://www.bbc.co.uk/news/uk-51768274">BBC</a>'s map of the UK that is colour-coded based on the total 7-day new cases per 100,000 population (incidence rate) which shows where the hotspots in the country are. Standardizing the data in this format is essential so that areas with different population sizes can be compared on an equal footing, but the number of days may differ according to jurisdiction, for example the European Union reports on a 14-day basis. However, the downside to BBC's map is that it only shows the snapshot of the current situation and leaves out the movement of the recent trend in order for us to gauge where the case trajectory is heading.
<p>
By combining the 7-day incidence rate with the 7-day average of new daily cases, we get a much clearer picture on the distinct trends in different regions; for example, we can see that London only has one peak compared to two in most areas in the north. This can be particularly useful when formulating a forecasting model for the whole country, since we may need to forecast these two categories of regions separately and add the outcome at the end, instead of using the total national figure as an input which ignores these underlying patterns.
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk1-incidence_and_trend.png?raw=true">
<p>
The colour scale used for the 7-day new cases per 100,000 population in the chart above and all others that follow is based on the BBC's palette.
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/scale_bbc.png?raw=true">
<p>
In contrast to the latest situation where a recovery trend is well underway, the chart below shows how the situation looked like on 9 Jan 2021 when the total UK daily cases reached its peak at 60,000. London, Liverpool and Essex all went off the charts with a 7-day incidence rate exceeding 1000 cases per 100,000 population. Regions in the south were hardest hit first before it spread further north; and as we would later observe, Midlands would be the last area to recover from the worst of the second wave.
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk1-incidence_and_trend_20210109.png?raw=true">
<p>  

### Identifying changes in new cases

While the charts above are great in conveying the trend over several weeks, it can be hard to identify the detailed movements over shorter periods of time, especially when the differences are relatively low. The chart below shows the breakdown of 7-day changes in new daily cases (by means of 7-day average), split by where cases are growing and where they are shrinking. This is also particularly important in the event where the total national case is flat, but caused by large pluses that are offset by large minuses - without for a clear picture of the underlying drivers behind the regional figures, we would be making the wrong conclusions.
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk2_changes_by_county.png?raw=true">
<p>
  
### Section 3
  
<p>Text
<p>
<img align="left" src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk3_incidence_rate_by_region.png?raw=true">
<p>
  
Text
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk4_incidence_rate_by_county.png?raw=true">
<p>

Text
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk7_changes_in_cases.png?raw=true">
<p>
  
Text
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk8_changes_in_hospitalization.png?raw=true">
<p>

Text
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk9-incidence_spread.png?raw=true">
<p>

Text
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk10-tier_spread.png?raw=true">
<p>

Text
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk11_model_first_wave.png?raw=true">
