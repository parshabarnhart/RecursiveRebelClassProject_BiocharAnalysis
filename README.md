# RecursiveRebelClassProject_BiocharAnalysis
library(ggplot2)
library(dplyr)
library(tidyr)
library(readr)
Seed_Germination_Study <- read_csv("C:/Users/17174/OneDrive/Desktop/PSU/STAT184/ProjectDataSets/Biochar_Germ_All_Species_For_SH_053118.csv")

str(Seed_Germination_Study)

Biochar_Germination_Study <- read_csv("C:/Users/17174/OneDrive/Desktop/PSU/STAT184/ProjectDataSets/Biochar_Germination_Study_Biochar_pH_EC_P.csv")

str(Biochar_Germination_Study)

Joined_Germination_Study <- join(Seed_Germination_Study, Biochar_Germination_Study, by = "pH")

head(Joined_Germination_Study)

  ggplot(Seed_Germination_Study) +
    aes(x = feedstock, y = aspercent) +
    geom_boxplot(fill = "#469AB4") +
    labs(
      x = "Biochar Feedstock",
      y = "Germination Percent",
      title = "Germination Percent by Biochar Feedstock"
    ) +
    theme_minimal()

    ggplot(Seed_Germination_Study) +
  aes(x = feedstock, y = shootdw) +
  geom_bar(stat = "summary", fun = "sum", fill = "#176C17") +
  labs(
    x = "Biochar Feedstock",
    y = "Mean Shoot Dry Weight (g)",
    title = "Average Shoot Dry Weight by Biochar Feedstock"
  ) +
  theme_minimal()

  Seed_Germination_Study %>%
  group_by(feedstock) %>%
  summarize(
    Mean_pH = mean(pH, na.rm = TRUE),
    Mean_EC = mean(EC, na.rm = TRUE),
    Mean_P = mean(P, na.rm = TRUE)
  )

  
