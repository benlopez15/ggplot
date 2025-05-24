# ggplot
Visualizations using ggplot for plant breeding data. 
################################################################################
Heat map visualizing grain yield data.
################################################################################
HM <- ggplot(data, aes(x = X.Row., y = Range)) +
  geom_tile(aes(fill = Weight..lb.), col = "white") +
  geom_text(aes(label = X.Line.), size = 2) +
  geom_tileborder(aes(group = 1, grp = X.Test.), lwd = 1.2) +
  scale_fill_viridis_c(option =  "plasma") +
  scale_x_continuous(breaks = seq(1,max(data$X.Row.), 1)) +
  scale_y_continuous(breaks = 1:max(data$Range)) +
  labs(x = "Row", y = "Range", title = "Heat Map ") +
  theme_classic() +
  theme(axis.text = element_text(size = 12),
        axis.title = element_text(size = 14),
        legend.title = element_text(size = 10),
        legend.text = element_text(size = 12))
HM

![Rplot](https://github.com/user-attachments/assets/dfb03ee9-489b-4bcd-93c0-ea17a5b34653)


################################################################################
#Comparing Environments with Violin Plots
################################################################################
loc <- ggplot(State, aes(x = Loc, y = GY, fill = factor(Loc,))) +
  geom_violin(trim = F, adjust = 1.5, alpha = 0.5) +
  geom_boxplot(width = 0.2, color = "black", 
               outlier.color = "black", fill = "white") +

  labs(title = "Grain Yield 2024",
       x = "Location", y = "Grain Yield",
       fill = NULL ) +
  theme_classic() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1, size = 14),
        legend.position = "bottom",
        legend.title = element_text(size = 12),
        legend.text = element_text(size = 12),
        plot.title = element_text(hjust = 0.5, size = 16, face = "bold"),
        axis.title.x = element_text(size = 14, face = "bold"),
        axis.title.y = element_text(size = 14, face = "bold")) +
  theme(axis.text.y = element_text(size = 14))
loc

################################################################################
#Distribution at multiple locations histogram
################################################################################
locHist <- ggplot(State, aes(GY, after_stat(density),  fill = factor(Loc,))) + 
  geom_histogram() + facet_wrap(~Loc, ncol = 3) +
  labs(title = "State Grain Yield Distribution 2024", 
                          x = "Grain Yield", y = "Density", fill = NULL) +
  theme_get() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1, size = 12),
        legend.position = "bottom",
        legend.title = element_text(size = 12),
        legend.text = element_text(size = 14, face = "bold"),
        plot.title = element_text(hjust = 0.5, size = 16, face = "bold"),
        axis.title.x = element_text(size = 14, face = "bold"),
        axis.title.y = element_text(size = 14, face = "bold")) +
  theme(axis.text.y = element_text(size = 14))
locHist
        
