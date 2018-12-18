---
title: Použití ovládacích prvků HTML5 v programových testech UI
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a603a662c9007ab3ee0e66df0b23959bfdce83fb
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896185"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Použití ovládacích prvků HTML5 v programových testech UI

Programové testy UI zahrnují podporu pro některé ovládací prvky jazyka HTML5, které jsou zahrnuty v aplikaci Internet Explorer 9 a Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

 **Požadavky**

-   Visual Studio Enterprise

> [!WARNING]
> Ve verzích před Internet Explorer 10 bylo možné spustit programové testy uživatelského rozhraní ve vyšší úrovni oprávnění ve srovnání s, proces aplikace Internet Explorer. Při spouštění programových testů UI v Internet Exploreru 10, programový test uživatelského rozhraní a proces aplikace Internet Explorer musí být na stejné úrovni oprávnění. Toto je kvůli lepšímu zabezpečení funkce AppContainer v Internet Exploreru 10.

> [!WARNING]
> Je-li vytvořit programový test uživatelského rozhraní v Internet Exploreru 10, nemusí spouštět, pomocí aplikace Internet Explorer 9 nebo Internet Explorer 8. Je to proto, že aplikace Internet Explorer 10 obsahuje ovládací prvky HTML5, jako je zvuk, Video, indikátor průběhu a posuvník. Tyto ovládací prvky jazyka HTML5 nejsou rozpoznány aplikací Internet Explorer 9 nebo Internet Explorer 8. Podobně váš programový test UI pomocí aplikace Internet Explorer 9 může zahrnovat některé ovládací prvky jazyka HTML5, které aplikace Internet Explorer 8 nerozpozná.

## <a name="audio-control"></a>Ovládací prvek zvuku

**Ovládací prvek zvuku:** akce na ovládacím prvku Audio HTML5 se správně se zaznamenávají a přehrát.

![HTML5 Audio ovládacího prvku](../test/media/codedui_html5_audio.png)

|Akce|Záznam|Generovaný kód|
|-|---------------|-|
|**Přehrát zvuk**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Přehrát \<name > zvuku od 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Hledání na určitou dobu ve zvukovém souboru**|Hledání \<name > zvuku 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Pozastavit zvuku**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Pozastavit \<name > zvuku v 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Ztlumit zvuk**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Ztlumit \<name > zvuku|HtmlAudio.Mute()|
|**Zrušit ztlumení zvuk**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Zrušit ztlumení \<name > zvuku|HtmlAudio.Unmute()|
|**Změnit hlasitost zvuku**|Nastavit hlasitost \<name > zvuku a 79 %|HtmlAudio.SetVolume(float)|

Zobrazit [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) pro seznam vlastností, na které můžete přidat kontrolní výraz.

 **Prohledat vlastnosti:** vlastnosti hledání pro `HtmlAudio` jsou `Id`, `Name` a `Title`.

 **Vlastnosti filtru:** vlastnosti filtru pro `HtmlAudio` jsou `Src`, `Class`, `ControlDefinition` a `TagInstance`.

> [!NOTE]
> Můžou být významné množství času pro hledání a pozastavit. Během přehrávání programového testu uživatelského rozhraní počká, až do zadaného času v `(TimeSpan)` před pozastavením zvuku. Pokud pomocí některé zvláštní okolnosti, určený čas uplynul před tím příkazu k pozastavení, bude vyvolána výjimka.


## <a name="video-control"></a>Ovládacího prvku video
 **Ovládacího prvku Video:** akce na ovládacím prvku jako videa HTML5 správně se zaznamenávají a přehrát.

 ![Ovládací prvek jako videa HTML5](../test/media/codedui_html5_video.png)

|Akce|Záznam|Generovaný kód|
|-|---------------|-|
|**Přehrát video**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Přehrát \<name > videa od 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Hledání na určitou dobu ve videu**|Hledání \<name > videa na 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Pozastavit video**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Pozastavit \<name > videa v 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Ztlumit videa**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Ztlumit \<name > videa|HtmlVideo.Mute()|
|**Zrušit ztlumení videa**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Zrušit ztlumení \<name > videa|HtmlVideo.Unmute()|
|**Změna hlasitosti videa**|Nastavit hlasitost \<name > videa a 79 %||

Zobrazit [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) pro seznam vlastností, na které můžete přidat kontrolní výraz.

 **Prohledat vlastnosti:** vlastnosti hledání pro `HtmlVideo` jsou `Id`, `Name` a `Title`.

 **Vlastnosti filtru:** vlastnosti filtru pro `HtmlVideo` jsou `Src`, `Poster`, `Class`, `ControlDefinition` a `TagInstance`.

> [!NOTE]
> Pokud rewind nebo rychlé převinutí vpřed videa pomocí-30s nebo +30s popisky, se budou agregovat hledání správný čas.

## <a name="progressbar"></a>ProgressBar
 **ProgressBar – ovládací prvek:** The ProgressBar je – interactable ovládací prvek. Můžete přidat kontrolní výrazy na `Value` a `Max` vlastnosti tohoto ovládacího prvku. Další informace najdete v tématu [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

 ![Ovládací prvek HTML5 ProgressBar](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Viz také:

- [Elementy HTML](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytvoření programové testy uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
