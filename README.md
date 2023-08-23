In questa pagina sono presenti delle ulteriori considerazioni su altri
fattori di rischio modificabili per la salute. In particolare, viene
valutato il consumo di alcol (nello specifico quello fuori dai pasti), e
viene approfondita la tematica del consumo di verdura, frutta e ortaggi.

## Consumo di alcolici

#### Andamento consumo alcolici fuori pasto

<img src="README_files/figure-markdown_github/unnamed-chunk-2-1.png" alt="Figura 1: Consumo alcolici fuori pasto dal 2012." width="70%" />
<p class="caption">
Figura 1: Consumo alcolici fuori pasto dal 2012.
</p>

Negli ultimi dieci anni il consumo di alcolici fuori pasto è aumentato
di sei punti percentuali. Questo porta ad alcolemia elevata ed è
associato a numerosi effetti cronici nocivi.

### Mappa consumo alcol

<img src="README_files/figure-markdown_github/unnamed-chunk-3-1.png" alt="Numero di individui che consumano alcol fuori pasto nel 2022, per 100 persone con le stesse caratteristiche." width="80%" />
<p class="caption">
Numero di individui che consumano alcol fuori pasto nel 2022, per 100
persone con le stesse caratteristiche.
</p>

Con riferimento al 2022, si notano delle differenze significative nel
consumo di alcol fuori dai pasti nelle diverse regioni. Risulta infatti
che nelle regioni del Mezzogiorno ci sia una minore propensione degli
abitanti a bere alcol fuori dai pasti, mentre specialmente in Trentino
Alto Adige, in Valle d’Aosta e in Friuli Venezia Giulia le percentuali
sono più elevate, arrivando a sfiorare il 50%.

### Consumo verdure, frutta ed ortaggi

#### Andamento consumo verdure, frutta ed ortaggi

<img src="README_files/figure-markdown_github/unnamed-chunk-4-1.png" alt="Figura 3: Andamento del consumo di verdure, ortaggi e frutta" width="90%" />
<p class="caption">
Figura 3: Andamento del consumo di verdure, ortaggi e frutta
</p>

Il consumo di almeno una delle tre tipologie considerate è diminuito del
4% nell’ultimo decennio, particolarmente evidente la discesa del consumo
di verdure dal 2017 ad oggi. Sembra invece stabile il consumo di frutta.

### Mappa consumo frutta

``` r
setwd("G:\\.shortcut-targets-by-id\\1u94QNKRHDFCa3IdeFJGkbvs-uG7zf3tE\\ISTAT_Poster\\Farmaci_titolo_studio\\pulito")
df<- as.data.frame(read_excel("VerduraMap.xlsx",
col_names= T, range = 'A1:H21'))
dimnames(df)[[2]][2:8]<- c("Verd>1", "Ort>1", "Frut>1", "General>1",
"OnlyOne", "TwoFour", "MoreThanFive")
df$regione <- ifelse(df$Territorio == "Puglia", "Apulia",
ifelse(df$Territorio == "Sicilia", "Sicily",
ifelse(df$Territorio == "Trentino Alto Adige", "Trentino-Alto Adige",

df$Territorio)))

df <- arrange(df, regione)

df_finale <- cbind(it_regions, df)
ggplot(data = df_finale)+
geom_sf(color = "black", aes(fill = df$`Frut>1`))+
scale_fill_viridis_c(option='viridis', na.value = 'grey80',

direction= -1,
begin=0,
limits= c(65, 80))+

ggtitle("")+
labs(fill = "")+
theme(panel.background = element_rect(fill = 'white'), # white background
panel.grid.major = element_blank(), # remove grid
panel.grid.minor = element_blank(), # remove grid
legend.key.size = unit(1, 'lines'), # Dimensions parameters
legend.text = element_text(size= 7),
legend.title = element_text(size= 2),
plot.title = element_text(size=2, hjust = 0.5))+
coord_sf(label_axes = "SW") # remove coordinates
```

![](README_files/figure-markdown_github/unnamed-chunk-5-1.png)

Dalla figura si nota che il consumo di frutta è in generale più elevato
rispetto al consumo di verdure e ortaggi, in tutto il Paese. In Umbria,
Calabria e Sardegna la percentuale di individui che consuma almeno una
porzione di frutta ogni giorno è la più elevata, arrivando quasi
all’80%. Viceversa, Valle d’Aosta, Lombardia, Veneto e Friuli Venezia
Giulia registrano le percentuali inferiori, attestandosi tra il 65 e il
70%.
