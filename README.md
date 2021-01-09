### Hello and Welcome to my world 🌎

Quick 5 things about me:

1. Final semester a the University of Queensland, majoring in Geogrpahical Sciences 🎓
2. Currently working on Bushfire Impacts on Vegetation using GIS and Remote Sensing 🛰️
3.
4.
5.

---
output: 
  pdf_document:
    latex_engine: pdflatex
    template: ~/Dropbox/miscelanea/svm-r-markdown-templates/svm-latex-cv.tex
geometry: margin=1in

title: "CV"
author: William Sealy Gosset

jobtitle: "Chief Brewer, Arthur Guinness & Son"
address: "Guinness Brewery · Park Royal · London NW10 7RR, UK"
fontawesome: yes
email: guinness@consumer-care.net
# github: svmiller
phone: "+353 1 408 4800"
web: guinness.com
updated: no

keywords: R Markdown, academic CV, template

fontfamily: mathpazo
fontfamilyoptions: sc, osf
fontsize: 11pt
linkcolor: blue
urlcolor: blue
---







# Education
University of Queensland <- read_csv("resume/job-titles.csv",
                      locale = locale(encoding = 'ISO-8859-1'),
                      col_types = cols(
                        begin = col_date("%m/%d/%y"),
                        end = col_date("%m/%d/%y")
                        )
)

# Job descriptions
job.descriptions <- read_csv("resume/job-descriptions.csv",
                      locale = locale(encoding = 'ISO-8859-1')
)
#> Parsed with column specification:
#> cols(
#>   jobId = col_double(),
#>   position = col_character(),
#>   employer = col_character(),
#>   accomplishments = col_character()
#> )

# Experience section
job.titles %>% 
  left_join(job.descriptions) %>% 
  vitae::detailed_entries(
    what = position,
    when = as.character(
      glue("{year(begin)} - {if_else(!is.na(end), as.character(year(end)), 'present')}")),
    with = employer,
    where = glue("{city}, {region}, {country}"),
    why = accomplishments) %>% 
  glimpse()
#> Joining, by = c("jobId", "position", "employer")
#> Observations: 7
#> Variables: 5
#> Groups: what, when, with, where [7]
#> $ what  <chr> "Post-doctoral Research Associate", "Graduate Research A...
#> $ when  <chr> "2016 - present", "2012 - 2016", "2014 - 2016", "2011 - ...
#> $ with  <chr> "University of Nebraska-Lincoln", "University of Florida...
#> $ where <S3: glue> "Lincoln, Nebraska, US", "Gainesville, Florida, US"...
#> $ why   <list> [<"Developed innovative approach to analyzing repeat-pu...




