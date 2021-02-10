---
title: Použití ovládacích prvků HTML5 v programových testech UI
description: Přečtěte si o podpoře programových testů uživatelského rozhraní pro ovládací prvky HTML5, které jsou součástí aplikace Internet Explorer 9 a Internet Explorer 10.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 931db4db8b6dd5b076ab720c866bb2b5b97aa15c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946355"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Použití ovládacích prvků HTML5 v programových testech UI

Programové testy UI zahrnují podporu pro některé ovládací prvky HTML5, které jsou součástí aplikace Internet Explorer 9 a Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise

> [!WARNING]
> Ve verzích starších než Internet Explorer 10 bylo možné spustit programové testy uživatelského rozhraní ve vyšší úrovni oprávnění v porovnání s verzí procesu Internet Exploreru. Při spouštění programových testů uživatelského rozhraní v aplikaci Internet Explorer 10 musí být programový test uživatelského rozhraní i proces aplikace Internet Explorer na stejné úrovni oprávnění. Důvodem je to, že aplikace Internet Explorer 10 nabízí bezpečnější funkce kontejneru AppContainer.

> [!WARNING]
> Pokud vytvoříte programový test uživatelského rozhraní v aplikaci Internet Explorer 10, nemusí se spustit pomocí aplikace Internet Explorer 9 nebo Internet Explorer 8. Je to proto, že aplikace Internet Explorer 10 obsahuje ovládací prvky HTML5, jako jsou zvuk, video, ProgressBar a posuvník. Tyto ovládací prvky jazyka HTML5 nejsou rozpoznány aplikací Internet Explorer 9 nebo Internet Explorer 8. Podobně váš programový test UI pomocí aplikace Internet Explorer 9 může zahrnovat některé ovládací prvky jazyka HTML5, které aplikace Internet Explorer 8 nerozpozná.

## <a name="audio-control"></a>Ovládání zvuku

**Ovládání zvuku:** Akce v ovládacím prvku zvuk HTML5 jsou správně zaznamenávány a přehrány.

![Ovládací prvek zvuku HTML5](../test/media/codedui_html5_audio.png)

|Akce|Nahrávání|Generovaný kód|
|-|---------------|-|
|**Přehrát zvuk**<br /><br /> Přímo z ovládacího prvku nebo z místní nabídky na ovládacím prvku.|Přehrát \<name> zvuk z 00:00:00|HtmlAudio. Play (TimeSpan)|
|**Vyhledat určitý čas ve zvukovém zařízení**|Vyhledat \<name> zvuk na 00:01:48|HtmlAudio. Seek (TimeSpan)|
|**Pozastavit zvuk**<br /><br /> Přímo z ovládacího prvku nebo z místní nabídky na ovládacím prvku.|Pozastavit \<name> zvuk v 00:01:53|HtmlAudio. Pause (TimeSpan)|
|**Ztlumení zvuku**<br /><br /> Přímo z ovládacího prvku nebo z místní nabídky na ovládacím prvku.|Ztlumení \<name> zvuku|HtmlAudio. Mute ()|
|**Zrušit ztlumení zvuku**<br /><br /> Přímo z ovládacího prvku nebo z místní nabídky na ovládacím prvku.|Zrušit ztlumení \<name> zvuku|HtmlAudio. ztlumení ()|
|**Změnit hlasitost zvuku**|Nastavit hlasitost \<name> zvuku na 79%|HtmlAudio. SetVolume (float)|

Seznam vlastností, na které lze přidat kontrolní výraz, naleznete v tématu [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) .

**Vlastnosti hledání:** Vlastnosti hledání pro `HtmlAudio` jsou `Id` `Name` a `Title` .

**Vlastnosti filtru:** Vlastnosti filtru pro `HtmlAudio` jsou `Src` , `Class` `ControlDefinition` a `TagInstance` .

> [!NOTE]
> Množství času pro hledání a pozastavení může být významné. Během přehrávání bude programový test uživatelského rozhraní čekat až do zadaného času `(TimeSpan)` před pozastavením zvuku. Pokud některý z zvláštních okolností, zadaný čas uplynul před tím, než dojde k provedení příkazu pozastavit, bude vyvolána výjimka.

## <a name="video-control"></a>Ovládací prvek video
**Ovládací prvek video:** Akce v ovládacím prvku video HTML5 jsou správně zaznamenávány a přehrány.

![Řízení videa HTML5](../test/media/codedui_html5_video.png)

|Akce|Nahrávání|Generovaný kód|
|-|---------------|-|
|**Přehrát video**<br /><br /> Přímo z ovládacího prvku nebo z místní nabídky na ovládacím prvku.|Přehrát \<name> video z 00:00:00|HtmlVideo. Play (TimeSpan)|
|**Vyhledat konkrétní čas ve videu**|Hledat \<name> video na 00:01:48|HtmlVideo. Seek (TimeSpan)|
|**Pozastavit video**<br /><br /> Přímo z ovládacího prvku nebo z místní nabídky na ovládacím prvku.|Pozastavit \<name> video v 00:01:53|HtmlVideo. Pause (TimeSpan)|
|**Ztlumení videa**<br /><br /> Přímo z ovládacího prvku nebo z místní nabídky na ovládacím prvku.|Ztlumení \<name> videa|HtmlVideo. Mute ()|
|**Zrušit ztlumení videa**<br /><br /> Přímo z ovládacího prvku nebo z místní nabídky na ovládacím prvku.|Zrušit ztlumení \<name> videa|HtmlVideo. ztlumení ()|
|**Změna objemu videa**|Nastavit hlasitost \<name> videa na 79%||

Seznam vlastností, na které lze přidat kontrolní výraz, naleznete v tématu [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) .

**Vlastnosti hledání:** Vlastnosti hledání pro `HtmlVideo` jsou `Id` `Name` a `Title` .

**Vlastnosti filtru:** Vlastnosti filtru pro `HtmlVideo` jsou `Src` ,, `Poster` a `Class` `ControlDefinition` `TagInstance` .

> [!NOTE]
> Pokud předáte převinutí nebo rychlé převinutí videa pomocí popisků-30 s nebo + 30 s, bude agregovaná, aby se vyhledal příslušný čas.

## <a name="progressbar"></a>ProgressBar
**Ovládací prvek ProgressBar:** Objekt ProgressBar je ovládací prvek, který nelze interaktivně používat. Můžete přidat kontrolní výrazy do `Value` `Max` vlastností a tohoto ovládacího prvku. Další informace najdete v tématu [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![Ovládací prvek HTML5 ProgressBar](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Viz také

- [HTML elementy](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytvořit kódované testy uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
