---
title       : "Shiny Application and Reproducible Pitch Final"
subtitle    : "Coursera - Devoloping Data Products Final Assignment" 
author      : "Nitesh Champaneri"
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Details of the Assignment 

This is a peer review assignment within the Coursera - Devoliping Data Products Final Assignment module.

Full Details can be found in the Instructions.Rmd file in the repo: 

--- .class #id 

## Data 

Data used is number of deaths within different countries:


# deaths <- read.csv("DeathsByCountry.csv", header = TRUE)
# summary(deaths)

 X                  USA           BRAZIL       AUSTRALIA      FRANCE           UK            CANADA       ITALY     
 Length:5           Min.   : 432   Min.   : 572   Min.   : 9   Min.   :12.0   Min.   :  0.0   Min.   : 4   Min.   : 3.0  
 Class :character   1st Qu.:1149   1st Qu.:1060   1st Qu.:14   1st Qu.:14.0   1st Qu.:  0.0   1st Qu.: 5   1st Qu.: 4.0  
 Mode  :character   Median :1234   Median :1175   Median :18   Median :17.0   Median :  8.0   Median : 6   Median : 6.0  
                    Mean   :1127   Mean   :1069   Mean   :16   Mean   :15.6   Mean   : 48.6   Mean   : 7   Mean   : 5.8  
                    3rd Qu.:1334   3rd Qu.:1262   3rd Qu.:18   3rd Qu.:17.0   3rd Qu.: 55.0   3rd Qu.: 6   3rd Qu.: 6.0  
                    Max.   :1486   Max.   :1274   Max.   :21   Max.   :18.0   Max.   :180.0   Max.   :14   Max.   :10.0  
     SPAIN          RUSSIA          INDIAN          PORTUGAL     NETHERLAND 
 Min.   : 1.0   Min.   : 70.0   Min.   : 834.0   Min.   :2.0   Min.   :0.0  
 1st Qu.: 1.0   1st Qu.:114.0   1st Qu.: 871.0   1st Qu.:2.0   1st Qu.:2.0  
 Median : 3.0   Median :124.0   Median : 942.0   Median :3.0   Median :2.0  
 Mean   : 7.2   Mean   :113.4   Mean   : 932.2   Mean   :3.2   Mean   :2.2  
 3rd Qu.: 5.0   3rd Qu.:129.0   3rd Qu.:1007.0   3rd Qu.:3.0   3rd Qu.:3.0  
 Max.   :26.0   Max.   :130.0   Max.   :1007.0   Max.   :6.0   Max.   :4.0  

--- .class #id 

## ui


ui <- fluidPage(
        
        titlePanel("Deaths"), 
        sidebarLayout(       
                         selectInput("Country", "Country",
                                     choices = colnames(deaths[-1])),
                         hr()),
            
            
        # Show a plot of the generated distribution
        mainPanel(
           plotOutput("Deaths")
        )
    )
)

--- .class #id 

## Server

server <- function(input, output) {

   output$Deaths <- renderPlot({
            
           barplot(deaths[,input$Country],
                xlab = 'Year',
                main = 'Deaths by Year',
                ylab = 'Number of Deaths')
       

    })
}



