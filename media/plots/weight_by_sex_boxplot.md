library(tidyverse)
library(plotly)
library(htmlwidgets)
p3 <- ggplot(bigclass, aes(x = sex, y = weight, fill = sex)) +
  geom_boxplot(alpha = 0.8) +
  scale_fill_manual(values = c('M' = '#0072B2', 'F' = '#D55E00')) +
  labs(title = 'Weight Distribution by Sex', x = 'Sex', y = 'Weight') +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 18, face = 'bold'),
    axis.title.x = element_text(size = 18),
    axis.title.y = element_text(size = 18),
    axis.text.x = element_text(size = 14),
    axis.text.y = element_text(size = 14),
    panel.background = element_rect(fill = 'white', colour = NA),
    plot.background = element_rect(fill = 'white', colour = NA),
    legend.position = 'none'
  )
p3_plotly <- ggplotly(p3)
saveWidget(p3_plotly, file = '/content/project/media/plots/weight_by_sex_boxplot.html', selfcontained = TRUE)
