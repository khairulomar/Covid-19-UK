# Alternative Analysis of Covid-19 in the UK
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

While the charts above are useful in conveying the trend over several weeks, it can be hard to identify detailed movements over shorter periods of time, especially when the differences are relatively small. The chart below shows the breakdown of week-on-week changes in new daily cases (by means of 7-day average), split by where cases are growing and where they are shrinking. This is also particularly important in the event where the total national case is flat, but is caused by large pluses (+) that are offset by large minuses (-); without a clear picture of the underlying pattern behind the regional figures, we would be making dangerously wrong conclusions.
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk2_changes_by_county.png?raw=true">
<p>
  
### Evolution of incidence rate
  
UK government has produced an  <a href="https://coronavirus.data.gov.uk/">interactive map</a> of the country that shows the evolution of total 7-day cases per 100,000 population as a measure of incidence rate. However, there is still an absence of a single-view visualization to assess this timeline evolution by region which is what I tried to produce in the two charts below, one showing the main regions of the UK, followed by additional breakdown by county. D1 to D4 in the charts refer to the key milestones, namely the start of the 3-tier system (D1), the start (D2) and the end (D3) of second England lockdown, and the start of the third England lockdown (D4).
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk3_incidence_rate_by_region.png?raw=true">
<p>
Similar set of data broken down by county for further deep dive, but with x- and y-axis swapped for better clarity:
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk4_incidence_rate_by_county.png?raw=true">
<p>

### Focus on week-on-week changes

Most visualizations are focused on the actual daily figures, but in many instances, it would be better to visualize them in the form of changes. For example, in determining the effectiveness of a lockdown, it can be more useful to focus on the changes as shown below as the week-on-week change of 7-day average of new cases which better highlights when cases are decreasing or increasing and at what magnitude. Similar use case can also be implemented in comparing the evolution of R number, but instead of using the absolute change in new cases, we can use the change in new cases as a percentage to be comparable with the method used in deriving R number.
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk7_changes_in_cases.png?raw=true">
<p>
Week-on-week changes in the number of Covid patients below can be compared with the previous chart, which highlights the time delay between the drop in new cases and the drop in hospitalization numbers.
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk8_changes_in_hospitalization.png?raw=true">
<p>

### Estimating case numbers when testing is limited

The BBC does a good job in highlighing that the number of offically reported cases prior to mid-May on their <a href="https://www.bbc.co.uk/news/uk-51768274">daily chart</a> is understated due to the targeted testing policy at the time, and therefore cannot be justifiably compared with figures when mass testing is available. However, the BBC does not show what the possible true rate might be during this stage, which I believe would be useful in order to make a comparison with the second wave. To achieve this, I have used hospitalization data from the NHS as a predictor, since it has proven to be more reliable indicator even when testing is limited. By employing a regression model on the new cases and hospitalization data during the second wave, I fed the hospitalization data from the first wave in order to gauge the possible true extent of positive cases at the time. Due to the delay between a positive test and the need for hospitalization, I time-shifted the hospitalization data by 2 weeks as an input which gave a colleration score of 92%.
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk11_model_first_wave.png?raw=true">
<p>

### Identifying the worst affected localities

The are multiple ways in assessing which localities in the UK are the worst affected, including using the number of total deaths, total hospitalization, or total cases (either as absolute number or per population size). I have added another way to address this by looking at the spread of its daily incidence rate by means of total 7-day cases and plotting them on a box-and-whiskers to visualize its median, quartiles, and maximum rates. For this purpose, only data from Aug is included after mass testing was truly widespread so that data at different times are fairly comparable. We can observe few patterns here: while Isle of Wight has seen some of the worst daily rates (1200+), this only happened for a very brief period of time, while during other times the rates are low at below 100 mark. Liverpool has among the highest median rates, and the spread of its quartile rates which spans to almost 500 shows that the city not only faced one of the worst rates, but also spans across a long timescale.
<p>
<img src="https://github.com/khairulomar/Covid-19-UK/blob/main/img/covid-uk9-incidence_spread.png?raw=true">
<p>
