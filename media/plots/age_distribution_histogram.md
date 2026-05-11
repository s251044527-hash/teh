library(tidyverse)
library(plotly)
library(htmlwidgets)
p1 <- ggplot(bigclass, aes(x = age)) +
  geom_histogram(binwidth = 1, fill = '#0072B2', color = 'white', alpha = 0.8) +
  labs(title = 'Distribution of Age', x = 'Age', y = 'Frequency') +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 18, face = 'bold'),
    axis.title.x = element_text(size = 18),
    axis.title.y = element_text(size = 18),
    axis.text.x = element_text(size = 14),
    axis.text.y = element_text(size = 14),
    panel.background = element_rect(fill = 'white', colour = NA),
    plot.background = element_rect(fill = 'white', colour = NA)
  )
p1_plotly <- ggplotly(p1)
saveWidget(p1_plotly, file = '/content/project/media/plots/age_distribution_histogram.html', selfcontained = TRUE)
