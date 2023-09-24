<template>
  <div class="flex-container">
    <div class="flex-item"><span class="about-title">IK BEN EEN ILLUSTRATOR</span>
<p>
Ik werk vanuit een gevoel van afzonderlijkheid van de wereld waarin ik leef. Er ontbreekt mij hier aan wonder. Door mijn illustraties wil ik de wereld rijker maken aan de wonderen.
</p>
 
<p>
We leven in een super materialistische wereld en de mystiek van het bestaan wordt ons naar mijn mening ontnomen. Graag wil ik mijn bovenstaande woorden toelichten. Tegenwoordig lijkt het erop dat wij als mensen overal een antwoord op hebben, de wetenschap heeft verklaring voor alles wat er in de wereld gebeurd.
</p>
 

Het gevoel van verwondering, dat is wat ik in mijn werkproces nastreef. Ik ben er van overtuigt dat verwondering goed is voor de menselijke ziel. Verwondering brengt ons terug in de tijd, wanneer we nog kleine kinderen waren en de wereld nog niet zo goed snapte - een staat van onschuld en niet weten- precies het tegenovergestelde toestand van de wetenschappelijke geest.

Dit gevoel roep ik op door middel van creëren van onalledaagse en geestige illustraties. Onalledaags omdat je in mijn werk weinig dagelijkste taferelen zult aantreffen, en geestig omdat mijn werk veelal lach op je gezicht zult toveren.
</div>
    <div class="flex-item">
    <img class="img-margin" src="/img/ikdiemaak.webp">
    <p>Ik ben een illustrator die voornamelijk werkt met grafiet en aquarel.
Ik combineer deze twee mediums aan de hand van wat ik wil vertellen. Met waterverf illustreer ik intuïtieve en mysterieuze taferelen, met grafietpotlood kan ik mijn intentie volledig richten op detail en mezelf verdwalen in de maakproces. Het gelaat heeft een belangrijke rol in mijn kunst om de intentie van verwondering te overbrengen. Het maakproces zelf is voor mij een spirituele belevenis. Intentie die in de tekening wordt gestopt is erg belangrijk.
Natuurlijk lukt dit niet altijd, maar het is wel mijn streven.
    </p>
    </div>
</div>
   
</template>
    
<style scoped>
.flex-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  text-align: justify;
  font-size: 14px;
  line-height: normal;
  padding: 10px;
  gap: 60px; /* Set gap between flex items */
}

.flex-item {
  flex: 1;
  max-width: 430px;
  box-sizing: border-box;
  padding: 10px;
}

.about-title {
  display: block;
  color: #FF4040;
  font-size: 20px;
  letter-spacing: 0.3rem;
  font-weight: bold;
  margin-bottom: 20px;
}

.img-margin {
  display: block;
  max-width: 100%;
  height: auto;
  margin-bottom: 45px;
}

@media (max-width: 400px) {
  .flex-container {
    flex-direction: column; /* Stack flex items on smaller screens */
    font-size: 16px;
  }
}
@media (width <= 930px)
{
  .about-title {
    font-size: 18px;
    white-space: nowrap;
  }
  .flex-container {
    color: #241800;
    text-align: left;
    gap:10px;
  }
}
@media (width < 768px) {
  .flex-container {
    font-size: 17px;
    flex-direction: column; /* Stack flex items on smaller screens */
    gap: 10px;
  }
  .flex-item {
    max-width: 100%;
  }
}

</style>