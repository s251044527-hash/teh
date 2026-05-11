library(tidyverse)
library(plotly)
library(htmlwidgets)
p4 <- ggplot(bigclass, aes(x = height, y = weight, color = sex)) +
  geom_point(alpha = 0.8, size = 3) +
  scale_color_manual(values = c('M' = '#0072B2', 'F' = '#D55E00')) +
  labs(title = 'Height vs Weight by Sex', x = 'Height', y = 'Weight') +
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
p4_plotly <- ggplotly(p4)
saveWidget(p4_plotly, file = '/content/project/media/plots/height_vs_weight_scatterplot.html', selfcontained = TRUE)
