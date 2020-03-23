---
title: Použití ovládacích prvků HTML5 v programových testech UI
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 13f5da784a43df5146a66ca868bb6add9a702906
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585584"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Použití ovládacích prvků HTML5 v kódovaných testech ui

Programové testy ui zahrnují podporu pro některé ovládací prvky HTML5, které jsou součástí aplikace Internet Explorer 9 a Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise

> [!WARNING]
> Ve verzích před aplikací Internet Explorer 10 bylo možné spustit kódované testy ui ve vyšší úrovni oprávnění ve srovnání s procesem aplikace Internet Explorer. Při spuštění programových testů ui v aplikaci Internet Explorer 10 musí být kódovaný test ui i proces aplikace Internet Explorer na stejné úrovni oprávnění. Důvodem je bezpečnější funkce AppContainer v aplikaci Internet Explorer 10.

> [!WARNING]
> Pokud v aplikaci Internet Explorer 10 vytvoříte kódovaný test ui, nemusí být spuštěn pomocí aplikace Internet Explorer 9 nebo Internet Explorer 8. Důvodem je, že aplikace Internet Explorer 10 obsahuje ovládací prvky HTML5, jako je zvuk, video, indikátor progressbar a posuvník. Tyto ovládací prvky jazyka HTML5 nejsou rozpoznány aplikací Internet Explorer 9 nebo Internet Explorer 8. Podobně váš programový test UI pomocí aplikace Internet Explorer 9 může zahrnovat některé ovládací prvky jazyka HTML5, které aplikace Internet Explorer 8 nerozpozná.

## <a name="audio-control"></a>Ovládání zvuku

**Ovládání zvuku:** Akce v ovládacím prvku HTML5 Audio jsou správně zaznamenány a přehrávány.

![Ovládací prvek HTML5 Audio](../test/media/codedui_html5_audio.png)

|Akce|Nahrávání|Generovaný kód|
|-|---------------|-|
|**Přehrávání zvuku**<br /><br /> Přímo z ovládacího prvku nebo z nabídky ovládacího prvku pravým tlačítkem myši.|Přehrát \<jméno> audio od 00:00:00|HtmlAudio.Play (timespan)|
|**Vyhledejte určitou dobu ve zvukovém**|Hledat \<jméno> Audio na 00:01:48|HtmlAudio.Seek (timespan)|
|**Pozastavení zvuku**<br /><br /> Přímo z ovládacího prvku nebo z nabídky ovládacího prvku pravým tlačítkem myši.|Pozastavení \<názvu> audio v 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Ztlumit zvuk**<br /><br /> Přímo z ovládacího prvku nebo z nabídky ovládacího prvku pravým tlačítkem myši.|Ztlumit \<název> audio|HtmlAudio.Mute()|
|**Zrušení ztlumení zvuku**<br /><br /> Přímo z ovládacího prvku nebo z nabídky ovládacího prvku pravým tlačítkem myši.|Zrušení ztlumení \<názvu> audio|HtmlAudio.Unmute()|
|**Změna hlasitosti zvuku**|Nastavení hlasitosti \<názvu> audio na 79 %|HtmlAudio.SetVolume(float)|

Seznam vlastností, ke kterým můžete přidat kontrolní výraz, naleznete v tématu [HTMLAudioElement.](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement)

**Vlastnosti vyhledávání:** Vlastnosti hledání `HtmlAudio` `Id`jsou `Name` `Title`a .

**Vlastnosti filtru:** Vlastnosti filtru `HtmlAudio` `Src`jsou `Class` `ControlDefinition` , `TagInstance`a .

> [!NOTE]
> Množství času pro Seek a Pause může být významné. Během přehrávání bude kódovaný test ui čekat až `(TimeSpan)` do zadaného času v před pozastavením zvuku. Pokud podle některých zvláštních okolností uplynul a zadaný čas před zasažením příkazu Pause, bude vyvolána výjimka.

## <a name="video-control"></a>Řízení videa
**Ovládání videa:** Akce v ovládacím prvku HTML5 Video jsou správně zaznamenány a přehrávány.

![Ovládací prvek Videa HTML5](../test/media/codedui_html5_video.png)

|Akce|Nahrávání|Generovaný kód|
|-|---------------|-|
|**Přehrát video**<br /><br /> Přímo z ovládacího prvku nebo z nabídky ovládacího prvku pravým tlačítkem myši.|Přehrát \<jméno> video od 00:00:00|HtmlVideo.Play (TimeSpan)|
|**Vyhledat konkrétní čas ve videu**|Hledat \<jméno> Video na 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Pozastavení videa**<br /><br /> Přímo z ovládacího prvku nebo z nabídky ovládacího prvku pravým tlačítkem myši.|Pozastavit \<název> video v 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Ztlumit video**<br /><br /> Přímo z ovládacího prvku nebo z nabídky ovládacího prvku pravým tlačítkem myši.|Ztlumit \<název> Video|HtmlVideo.Mute()|
|**Zrušení ztlumení videa**<br /><br /> Přímo z ovládacího prvku nebo z nabídky ovládacího prvku pravým tlačítkem myši.|Zrušení ztlumení \<názvu> video|HtmlVideo.Unmute()|
|**Změna hlasitosti videa**|Nastavit hlasitost \<názvu> video na 79 %||

Seznam vlastností, ke kterým můžete přidat kontrolní výraz, naleznete v tématu [HTMLVideoElement.](https://developer.mozilla.org/docs/Web/HTML/Element/video)

**Vlastnosti vyhledávání:** Vlastnosti hledání `HtmlVideo` `Id`jsou `Name` `Title`a .

**Vlastnosti filtru:** Vlastnosti filtru `HtmlVideo` `Src`jsou `Poster` `Class`, `ControlDefinition` `TagInstance`, a .

> [!NOTE]
> Pokud video převinnete nebo přetočíte vpřed pomocí štítků -30s nebo +30s, bude to agregováno tak, aby se vyhledalo na vhodný čas.

## <a name="progressbar"></a>ProgressBar
**Ovládací prvek ProgressBar:** ProgressBar je neinteragovatelný ovládací prvek. Můžete přidat kontrolní výrazy na `Value` vlastnosti a `Max` tohoto ovládacího prvku. Další informace naleznete v tématu [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![Ovládací prvek Html5 ProgressBar](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Viz také

- [Elementy HTML](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Vytvoření kódovaných testů ui](../test/use-ui-automation-to-test-your-code.md)
- [Podporované konfigurace a platformy pro kódované testy a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
