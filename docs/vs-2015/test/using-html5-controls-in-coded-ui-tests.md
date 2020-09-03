---
title: Použití ovládacích prvků HTML5 v programových testech UI | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 029b547102863f4798ad261deb678c4d98596916
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657207"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Použití ovládacích prvků HTML5 v programových testech UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programové testy UI zahrnují podporu pro některé ovládací prvky HTML5, které jsou součástí aplikace Internet Explorer 9 a Internet Explorer 10.

 **Požadavky**

- Visual Studio Enterprise

> [!WARNING]
> Ve verzích starších než Internet Explorer 10 bylo možné spustit programové testy uživatelského rozhraní ve vyšší úrovni oprávnění v porovnání s verzí procesu Internet Exploreru. Při spouštění programových testů uživatelského rozhraní v aplikaci Internet Explorer 10 musí být programový test uživatelského rozhraní i proces aplikace Internet Explorer na stejné úrovni oprávnění. Důvodem je to, že aplikace Internet Explorer 10 nabízí bezpečnější funkce kontejneru AppContainer.

> [!WARNING]
> Pokud vytvoříte programový test uživatelského rozhraní v aplikaci Internet Explorer 10, nemusí se spustit pomocí aplikace Internet Explorer 9 nebo Internet Explorer 8. Je to proto, že aplikace Internet Explorer 10 obsahuje ovládací prvky HTML5, jako jsou zvuk, video, ProgressBar a posuvník. Tyto ovládací prvky jazyka HTML5 nejsou rozpoznány aplikací Internet Explorer 9 nebo Internet Explorer 8. Podobně váš programový test UI pomocí aplikace Internet Explorer 9 může zahrnovat některé ovládací prvky jazyka HTML5, které aplikace Internet Explorer 8 nerozpozná.

## <a name="supported-html5-controls"></a>Podporované ovládací prvky HTML5
 Programové testy uživatelského rozhraní zahrnují podporu pro záznam, přehrávání a ověření následujících ovládacích prvků HTML5:

- [Ovládání zvuku](#audio-control)

- [Ovládací prvek video](#video-control)

- [Posuvník](#slider)

- [ProgressBar](#progressbar)

### <a name="audio-control"></a>Ovládání zvuku
 **Ovládání zvuku:** Akce v ovládacím prvku zvuk HTML5 jsou správně zaznamenávány a přehrány.

 ![Ovládací prvek zvuku HTML5](../test/media/codedui-html5-audio.png)

|Akce|Nahrávání|Generovaný kód|
|------------|---------------|--------------------|
|**Přehrát zvuk**<br /><br /> Přímo z ovládacího prvku Control nebo z kontextové nabídky ovládací prvky.|Přehrát \<name> zvuk z 00:00:00|HtmlAudio. Play (TimeSpan)|
|**Vyhledat určitý čas ve zvukovém zařízení**|Vyhledat \<name> zvuk na 00:01:48|HtmlAudio. Seek (TimeSpan)|
|**Pozastavit zvuk**<br /><br /> Přímo z ovládacího prvku Control nebo z kontextové nabídky ovládací prvky.|Pozastavit \<name> zvuk v 00:01:53|HtmlAudio. Pause (TimeSpan)|
|**Ztlumení zvuku**<br /><br /> Přímo z ovládacího prvku Control nebo z kontextové nabídky ovládací prvky.|Ztlumení \<name> zvuku|HtmlAudio. Mute ()|
|**Zrušit ztlumení zvuku**<br /><br /> Přímo z ovládacího prvku Control nebo z kontextové nabídky ovládací prvky.|Zrušit ztlumení \<name> zvuku|HtmlAudio. ztlumení ()|
|**Změnit hlasitost zvuku**|Nastavit hlasitost \<name> zvuku na 79%|HtmlAudio. SetVolume (float)|

 Pro HtmlAudio jsou k dispozici následující vlastnosti a můžete do nich přidat kontrolní výraz:

```
string AutoPlay
string Controls
string CurrentSrc
string CurrentTime
string CurrentTimeAsString
string Duration
string DurationAsString
string Ended
string Loop
string Muted
string Paused
string PlaybackRate
string ReadyState
string Seeking
string Src
string Volume
```

 **Vlastnosti hledání:** Vlastnosti hledání pro `HtmlAudio` jsou `Id` `Name` a `Title` .

 **Vlastnosti filtru:** Vlastnosti filtru pro `HtmlAudio` jsou `Src` , `Class` `ControlDefinition` a `TagInstance` .

> [!NOTE]
> Množství času pro hledání a pozastavení může být významné. Během přehrávání bude programový test uživatelského rozhraní čekat až do zadaného času `(TimeSpan)` před pozastavením zvuku. Pokud některý z zvláštních okolností, zadaný čas uplynul před tím, než dojde k provedení příkazu pozastavit, bude vyvolána výjimka.

### <a name="video-control"></a>Ovládací prvek video
 **Ovládací prvek video:** Akce v ovládacím prvku video HTML5 jsou správně zaznamenávány a přehrány.

 ![Řízení videa HTML5](../test/media/codedui-html5-video.png)

|Akce|Nahrávání|Generovaný kód|
|------------|---------------|--------------------|
|**Přehrát video**<br /><br /> Přímo z ovládacího prvku Control nebo z kontextové nabídky ovládací prvky.|Přehrát \<name> video z 00:00:00|HtmlVideo. Play (TimeSpan)|
|**Vyhledat konkrétní čas ve videu**|Hledat \<name> video na 00:01:48|HtmlVideo. Seek (TimeSpan)|
|**Pozastavit video**<br /><br /> Přímo z ovládacího prvku Control nebo z kontextové nabídky ovládací prvky.|Pozastavit \<name> video v 00:01:53|HtmlVideo. Pause (TimeSpan)|
|**Ztlumení videa**<br /><br /> Přímo z ovládacího prvku Control nebo z kontextové nabídky ovládací prvky.|Ztlumení \<name> videa|HtmlVideo. Mute ()|
|**Zrušit ztlumení videa**<br /><br /> Přímo z ovládacího prvku Control nebo z kontextové nabídky ovládací prvky.|Zrušit ztlumení \<name> videa|HtmlVideo. ztlumení ()|
|**Změna objemu videa**|Nastavit hlasitost \<name> videa na 79%||

 Všechny vlastnosti HtmlAudio jsou k dispozici pro HtmlVideo. Kromě toho jsou k dispozici také následující tři vlastnosti. Kontrolní výraz lze přidat na všechny z nich.

```
string Poster
string VideoHeight
string VideoWidth

```

 **Vlastnosti hledání:** Vlastnosti hledání pro `HtmlVideo` jsou `Id` `Name` a `Title` .

 **Vlastnosti filtru:** Vlastnosti filtru pro `HtmlVideo` jsou `Src` ,, `Poster` a `Class` `ControlDefinition` `TagInstance` .

> [!NOTE]
> Pokud předáte převinutí nebo rychlé převinutí videa pomocí popisků-30 s nebo + 30 s, bude agregovaná, aby se vyhledal příslušný čas.

### <a name="slider"></a>Posuvník
 **Ovládací prvek posuvníku:** Akce na ovládacím prvku posuvník HTML5 jsou správně zaznamenávány a přehrány.

 ![Ovládací prvek posuvník HTML5](../test/media/codedui-html5-slider.png)

|Akce|Nahrávání|Generovaný kód|
|------------|---------------|--------------------|
|**Nastavení pozice posuvníku**|Nastavit pozici na \<x> \<name> posuvník|HtmlSlider. ValueAsNumber =\<x>|

 Pro HtmlSlider jsou k dispozici následující vlastnosti a je možné do nich přidat kontrolní výraz:

```
string Disabled
string Max
string Min
string Required
string Step
string ValueAsNumber
```

### <a name="progressbar"></a>ProgressBar
 **Ovládací prvek ProgressBar:** Objekt ProgressBar je ovládací prvek, který nelze interaktivně používat. Můžete přidat kontrolní výrazy do `Value` `Max` vlastností a tohoto ovládacího prvku.

 ![Ovládací prvek HTML5 ProgressBar](../test/media/codedui-html5-progressbar.png)

## <a name="see-also"></a>Viz také

- [HTML elementy](https://www.w3schools.com/HTML/html_elements.asp)
- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytváření programových testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Přizpůsobení kódovaného testu uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
