library(tidyverse)
library(plotly)
library(htmlwidgets)
avg_math_by_sex <- bigclass %>% group_by(sex) %>% summarise(avg_math = mean(Math, na.rm = TRUE))
p2 <- ggplot(avg_math_by_sex, aes(x = sex, y = avg_math, fill = sex)) +
  geom_bar(stat = 'identity') +
  scale_fill_manual(values = c('M' = '#0072B2', 'F' = '#D55E00')) +
  labs(title = 'Average Math Score by Sex', x = 'Sex', y = 'Average Math Score') +
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
p2_plotly <- ggplotly(p2)
saveWidget(p2_plotly, file = '/content/project/media/plots/avg_math_by_sex.html', selfcontained = TRUE)
