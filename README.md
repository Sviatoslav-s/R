# #1
zarobki <- c(jan=2300, tomek=1800, maciek=4500, grzegorz=3700, bartek=1300, kacper=7200, janusz=6100)
zarobki
min(zarobki)
length(zarobki)
mean(zarobki)

#2
hotele <- read.table(file="C:\\Users\\barto\\Desktop\\europa_hotel.csv", sep=",", dec=".",header=TRUE)
hotele

#3
head(hotele,3)
tail(hotele,3)
names(hotele)

#4
gener <- hotele %>%
  select(Gender)
gener

#5
clean <- hotele %>%
    mutate(isCleanliness=if_else(Cleanliness>=3,"tak","nie"))
clean

#6
sredni <- hotele %>%
  summarise(sredni_wynik=round(mean(Food.and.drink),2))
sredni

#7 ?
uporz <- hotele %>%
  group_by(purpose_of_travel) %>%
  count(purpose_of_travel)
uporz

#8 ?
wektor_imie <- hotele %>%
  group_by(Type.Of.Booking) %>%
  select(Type.Of.Booking) %>%
  count()
wektor_imie  

stay <- hotele %>%
  group_by(Stay.comfort) %>%
  count()
stay
#9 wykres
# barplot(stay, main="Quality",xlab="Oś x", ylab="Oś y", col= c("red","lightgreen","orange", "lightblue"))
#10
colnames(hotele) <- gsub("\\.+", "_", colnames(hotele))
hotele
#11

podatek <- function(kwota)
{
  print(paste("Od ",kwota," złotych należy zapłacić ", round(kwota*0.13,2)," złotych podatku."))
}
podatek(100)

czyNieparzysta <- function(liczba)
{
  if(liczba%%2==0)
  {
    print("Uwaga! Liczba jest parzysta!")
  } else {
    print(liczba-3)
  }
}
czyNieparzysta(10)
czyNieparzysta(11)
