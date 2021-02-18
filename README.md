# Retos-Bedu


library(DBI)
library(RMySQL)

queries.R <- dbConnect(
  drv = RMySQL::MySQL(),
  dbname = "shinydemo",
  host = "shiny-demo.csa7qlmguqrf.us-east-1.rds.amazonaws.com",
  username = "guest",
  password = "guest")

Resultado <- dbGetQuery(queries.R, "SELECT CountryCode, Percentage, Language FROM CountryLanguage")

Filtro <- Resultado %>% filter (Language == "Spanish")

Espanol <- as.data.frame(Filtro)
