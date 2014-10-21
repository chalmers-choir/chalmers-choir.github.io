---
title: E-postbekräftelse
category: auditions
---

## Hitta till Rules

När vi skickar e-postbekräftelse att man har bokat audition, så använder vi oss av `Rules`.

För att hitta till regeln som styr e-postbekräftelse går vi till `Konfiguration`:

[![Välj Konfiguration](/images/configuration.png)](/images/configuration.png)

Sedan väljer vi rules:

[![Välj Rules](/images/rules.png)](/images/rules.png)

Alternativt så går man på adressen `/admin/config/workflow/rules`.

Här ser vi vilka regler vi har och vilka som är aktiverade:

[![Välj regeln 'Send e-mail to audition'](/images/rules_email.png)](/images/rules_email.png)

Regeln som heter `Send e-mail to audition` är den som styr e-postbekräftelsen.

## Send e-mail to audition

Här ser vi vad regeln består av:

[![Sammanfattning av regeln](/images/rules_email_summary.png)](/images/rules_email_summary.png)

Sammanfattar man regeln så kan vi se att regeln sätts igång av event `After saving a new registration`, alltså när någon registrerar sig.

Vi ser också under `Conditions` att den bara gäller när det är av typen `Auditions`.

Under `Åtgärder` ser vi vad som skall göras när allt detta är uppfyllt. Den hämtar registreringen och sedan kör den `Send mail`.

Klickar man på `Send mail` kan man se alla inställningar för just e-postmeddelandet.

## E-postinställningar

Så här ser sidan ut för själva e-postmeddelandet:

[![Inställningar skicka e-post](/images/rules_email_settings.png)](/images/rules_email_settings.png)

Till att börja med så kan vi säga att det finns lite variabler tillgängliga. `registration` är till exempel en sådan variabel. Den innehåller all information om den registrering som precis har skapats.

Trycker man på `replacement patterns` så ser man vad det finns för variabler tillgängliga att använda på respektive fält.

Sedan gällande all text som anges, så anges det alltid på svenska. Drupal är konfigurerat så att all text kommer bli mappad till svenska. När man vill ha fler språk, t. ex. engelska, så utgår systemet från svenska gör en översättning. Översättningen är manuell, EJ automatisk.

### Till

Vilken e-postadress vi skall skicka till. Här anger vi den e-postadress man använt när man registrerade sig `[registration:mail]`.

### Ämne

Här anger vi vilket ämne e-postmeddelandet skall ha. Här använder vi två variabler `[associated-node:title]` och `[site:name]`. Om vi använt oss av `Audition` som titel på nod, så är det `[associated-node:title]`. `[site:name]` är det som har satts i Drupals konfiguration och är i dagsläget `Chalmers Sångkör`.

### Meddelande

Här är själva texten i e-postmeddelandet. Här använder vi bland annat information om noden; url, titel och tid. Vi använder även namnet på den som registrerat sig.

Märk väl att texten skall vara på svenska och engelsk text gör man i översättningsgränssnittet.

### From

Vilket e-postadress som meddelandet skall komma ifrån. Vill man ha samma e-postadress som sidan använder sig av `choir@chs.chalmers.se` lämnar man fältet blankt.
