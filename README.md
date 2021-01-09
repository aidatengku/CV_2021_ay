### Hello and Welcome to my world 🌎

Quick 5 things about me:

1. Final semester a the University of Queensland, majoring in Geogrpahical Sciences 🎓
2. Currently working on Bushfire Impacts on Vegetation using GIS and Remote Sensing 🛰️
3.
4.
5.

---

title: "CV"
author: Aida Yamini Tengku 
jobtitle: "Graduate of Geographical Sciences from University of Queensland "
address: "Brisbane, Australia"
fontawesome: yes
# github: svmiller

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

# Relevant Work Experience 
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

# Relevant Work Experience 
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
#> $ what  <chr> "Geologist Trainee"
#> $ when  <chr> "July 2016"
#> $ with  <chr> "G&P Geotechnics Sdn Bhd"
#> $ where <S3: glue> "Kuala Lumpur, Malaysia"
#> $ why   <list> [<"Primary on-site representative for soil and core logging for a highway construction project">]




