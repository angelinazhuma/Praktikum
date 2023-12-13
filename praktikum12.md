## Praktikum 12
Väga huvitav praktikum, mulle meeldis rohkem kui kõik teised :)

# Ulesanne 3
```
echo "Sisesta oma nimi:"
read nimi
echo "Sisesta oma eriala:"
read eriala
echo "Sisesta oma matriklinumber:"
read matriklinumber

echo "Sinu nimi on: $nimi"
echo "Sinu eriala on $eriala"
echo "Sinu matriklinumber on $matriklinumber"
```

<img width="319" alt="Screenshot 2023-12-13 213708" src="https://github.com/angelinazhuma/Praktikum/assets/145142791/fb893037-03b2-4410-a0c7-d42ce43fca11">

# Ulesanne 4

#if [ "$#" -ne 2 ]; then
  echo "Kasutamine: $0 <algne_laiend> <uus_laiend>"
  exit 1
fi
algne_laiend=$1
uus_laiend=$2

for fail in *.$algne_laiend; do
  if [ -f "$fail" ]; then
    if [ "${fail##*.}" = "$algne_laiend" ]; then
      uus_fail=${fail/$algne_laiend/$uus_laiend}
      mv "$fail" "$uus_fail"
      echo "Fail ümbernimetatud: $fail -> $uus_fail"
    fi
  fi
done
<img width="282" alt="Screenshot 2023-12-13 220549" src="https://github.com/angelinazhuma/Praktikum/assets/145142791/32b1450d-90fb-4c7b-86e4-b392fc7a6213">

# Ulesanne 5
#!/bin/bash

if [ "$#" -ne 1 ]; then
  echo "Kasutamine: $0 <protsessi_nimi>"
  exit 1
fi
protsessi_nimi=$1
IFS=$'\n'
for line in $(ps -A | grep "$protsessi_nimi"); do
  cleaned_line=$(echo " $line" | tr -s ' ')
  protsessi_pid=$(echo "$cleaned_line" | awk '{print $1}')
  protsessi_nimi=$(echo "$cleaned_line" | awk '{print $NF}')

  echo "Protsess: $protsessi_nimi, PID: $protsessi_pid"
done
>
<img width="277" alt="Screenshot 2023-12-13 223603" src="https://github.com/angelinazhuma/Praktikum/assets/145142791/4d3830b7-02af-41d1-a8b4-67e3dbf17139">

# Ulesanne 6
#!/bin/bash

astenda() {
  local alus=$1
  local eksponent=$2
  local tulemus=1

  for ((i=1; i<=$eksponent; i++)); do
    tulemus=$((tulemus * alus))
  done

  echo $tulemus
}

alus=9
eksponent=5
tulemus=$(astenda $alus $eksponent)

echo "9^5 = $tulemus"
<img width="460" alt="Screenshot 2023-12-13 222258" src="https://github.com/angelinazhuma/Praktikum/assets/145142791/83755054-b944-4f11-9070-6ad093d47a44">

# Ulesanne 7
<img width="960" alt="Screenshot 2023-12-13 222742" src="https://github.com/angelinazhuma/Praktikum/assets/145142791/67abf2a1-5ac6-4d68-948e-a7d548c12269">
<img width="960" alt="Screenshot 2023-12-13 222752" src="https://github.com/angelinazhuma/Praktikum/assets/145142791/9091284a-f0d1-4bb8-9ece-bb3a00cf683a">

