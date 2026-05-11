library(tidyverse)
library(plotly)
library(qcc)
library(htmlwidgets)
filtered_data <- X034 %>% filter(Machine == 1, Temperature == 303, Pressure == 100)
part_length_data <- filtered_data$PartLength
mean_part_length <- mean(part_length_data, na.rm = TRUE)
median_part_length <- median(part_length_data, na.rm = TRUE)
std_dev_part_length <- sd(part_length_data, na.rm = TRUE)
# Conditional logic for qcc and limits would be here if regenerating R code from markdown
plot_data <- data.frame(Observation = 1:length(part_length_data), PartLength = part_length_data)
p5 <- ggplot(plot_data, aes(x = Observation, y = PartLength)) +
  geom_line(color = '#0072B2') +
  geom_point(color = '#0072B2', size = 2) +
  labs(
    title = 'Xbar One Control Chart for Part Length',
    x = 'Observation Number',
    y = 'Part Length'
  ) +
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
# Conditional addition of control lines and annotations
p5_plotly <- ggplotly(p5)
saveWidget(p5_plotly, file = '/content/project/media/plots/xbar_one_control_chart.html', selfcontained = TRUE)
