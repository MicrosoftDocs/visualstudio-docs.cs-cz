---
title: Použití ovládacích prvků HTML5 v programových testů UI | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: gewarren
manager: douge
ms.openlocfilehash: 92ee95d4840ab9a833adc1b0060117f0d6b94fbd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254459"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Použití ovládacích prvků HTML5 v programových testech UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programové testy UI zahrnují podporu pro některé ovládací prvky jazyka HTML5, které jsou zahrnuty v aplikaci Internet Explorer 9 a Internet Explorer 10.  
  
 **Požadavky**  
  
-   Visual Studio Enterprise  
  
> [!WARNING]
>  Ve verzích před Internet Explorer 10 bylo možné spustit programové testy uživatelského rozhraní ve vyšší úrovni oprávnění ve srovnání s, proces aplikace Internet Explorer. Při spouštění programových testů UI v Internet Exploreru 10, programový test uživatelského rozhraní a proces aplikace Internet Explorer musí být na stejné úrovni oprávnění. Toto je kvůli lepšímu zabezpečení funkce AppContainer v Internet Exploreru 10.  
  
> [!WARNING]
>  Je-li vytvořit programový test uživatelského rozhraní v Internet Exploreru 10, nemusí spouštět, pomocí aplikace Internet Explorer 9 nebo Internet Explorer 8. Je to proto, že aplikace Internet Explorer 10 obsahuje ovládací prvky HTML5, jako je zvuk, Video, indikátor průběhu a posuvník. Tyto ovládací prvky jazyka HTML5 nejsou rozpoznány aplikací Internet Explorer 9 nebo Internet Explorer 8. Podobně váš programový test UI pomocí aplikace Internet Explorer 9 může zahrnovat některé ovládací prvky jazyka HTML5, které aplikace Internet Explorer 8 nerozpozná.  
  
## <a name="supported-html5-controls"></a>Ovládací prvky jazyka HTML5 podporované  
 Programové testy UI podporují záznam, přehrávání a ověřování následující ovládací prvky jazyka HTML5 následující možnosti:  
  
-   [Ovládací prvek zvuku](#UsingHTML5ControlsCodedUITestsAudio)  
  
-   [Ovládacího prvku video](#UsingHTML5ControlsCodedUITestsVideo)  
  
-   [Posuvník](#UsingHTML5ControlsCodedUITestsSlider)  
  
-   [ProgressBar](#UsingHTML5ControlsCodedUITestsProgressBar)  
  
###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Ovládací prvek zvuku  
 **Ovládací prvek zvuku:** akce na ovládacím prvku Audio HTML5 se správně se zaznamenávají a přehrát.  
  
 ![Audio HTML5 se ovládací prvek](../test/media/codedui-html5-audio.png "CodedUI_HTML5_Audio")  
  
|Akce|Záznam|Generovaný kód|  
|------------|---------------|--------------------|  
|**Přehrát zvuk**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Přehrát \<name > zvuku od 00:00:00|HtmlAudio.Play(TimeSpan)|  
|**Hledání na určitou dobu ve zvukovém souboru**|Hledání \<name > zvuku 00:01:48|HtmlAudio.Seek(TimeSpan)|  
|**Pozastavit zvuku**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Pozastavit \<name > zvuku v 00:01:53|HtmlAudio.Pause(TimeSpan)|  
|**Ztlumit zvuk**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Ztlumit \<name > zvuku|HtmlAudio.Mute()|  
|**Zrušit ztlumení zvuk**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Zrušit ztlumení \<name > zvuku|HtmlAudio.Unmute()|  
|**Změnit hlasitost zvuku**|Nastavit hlasitost \<name > zvuku a 79 %|HtmlAudio.SetVolume(float)|  
  
 Následující vlastnosti jsou k dispozici pro HtmlAudio a pro všechny z nich můžete přidat kontrolní výraz:  
  
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
  
 **Prohledat vlastnosti:** vlastnosti hledání pro `HtmlAudio` jsou `Id`, `Name` a `Title`.  
  
 **Vlastnosti filtru:** vlastnosti filtru pro `HtmlAudio` jsou `Src`, `Class`, `ControlDefinition` a `TagInstance`.  
  
> [!NOTE]
>  Můžou být významné množství času pro hledání a pozastavit. Během přehrávání programového testu uživatelského rozhraní počká, až do zadaného času v `(TimeSpan)` před pozastavením zvuku. Pokud pomocí některé zvláštní okolnosti, určený čas uplynul před tím příkazu k pozastavení, bude vyvolána výjimka.  
  
###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a> Ovládacího prvku video  
 **Ovládacího prvku Video:** akce na ovládacím prvku jako videa HTML5 správně se zaznamenávají a přehrát.  
  
 ![Ovládací prvek jako videa HTML5](../test/media/codedui-html5-video.png "CodedUI_HTML5_Video")  
  
|Akce|Záznam|Generovaný kód|  
|------------|---------------|--------------------|  
|**Přehrát video**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Přehrát \<name > videa od 00:00:00|HtmlVideo.Play(TimeSpan)|  
|**Hledání na určitou dobu ve videu**|Hledání \<name > videa na 00:01:48|HtmlVideo.Seek(TimeSpan)|  
|**Pozastavit video**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Pozastavit \<name > videa v 00:01:53|HtmlVideo.Pause(TimeSpan)|  
|**Ztlumit videa**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Ztlumit \<name > videa|HtmlVideo.Mute()|  
|**Zrušit ztlumení videa**<br /><br /> Přímo z ovládacího prvku, nebo z místní nabídky ovládací prvky.|Zrušit ztlumení \<name > videa|HtmlVideo.Unmute()|  
|**Změna hlasitosti videa**|Nastavit hlasitost \<name > videa a 79 %||  
  
 Všechny vlastnosti HtmlAudio jsou k dispozici pro HtmlVideo. Kromě toho jsou následující tři vlastnosti také k dispozici. Kontrolní výraz lze přidat na všechny z nich.  
  
```  
string Poster  
string VideoHeight  
string VideoWidth  
  
```  
  
 **Prohledat vlastnosti:** vlastnosti hledání pro `HtmlVideo` jsou `Id`, `Name` a `Title`.  
  
 **Vlastnosti filtru:** vlastnosti filtru pro `HtmlVideo` jsou `Src`, `Poster`, `Class`, `ControlDefinition` a `TagInstance`.  
  
> [!NOTE]
>  Pokud rewind nebo rychlé převinutí vpřed videa pomocí-30s nebo +30s popisky, se budou agregovat hledání správný čas.  
  
###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a> Posuvník  
 **Ovládací prvek posuvník:** akcí v ovládacím prvku posuvník HTML5 správně se zaznamenávají a přehrát.  
  
 ![Ovládací prvek posuvník HTML5](../test/media/codedui-html5-slider.png "CodedUI_HTML5_Slider")  
  
|Akce|Záznam|Generovaný kód|  
|------------|---------------|--------------------|  
|**Nastavení pozice v posuvníku**|Nastavit pozici \<x > v \<name > posuvník|HtmlSlider.ValueAsNumber=\<x>|  
  
 Následující vlastnosti jsou k dispozici pro HtmlSlider a kontrolní výraz lze přidat na všechny z nich:  
  
```  
string Disabled  
string Max  
string Min  
string Required  
string Step  
string ValueAsNumber  
```  
  
###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a> Ovládací prvek ProgressBar  
 **Ovládací prvek ProgreesBar:** The ProgressBar je – interactable ovládací prvek. Můžete přidat kontrolní výrazy na `Value` a `Max` vlastnosti tohoto ovládacího prvku.  
  
 ![Ovládací prvek HTML5 ProgressBar](../test/media/codedui-html5-progressbar.png "CodedUI_HTML5_ProgressBar")  
  
## <a name="see-also"></a>Viz také  
 [Elementy HTML](http://go.microsoft.com/fwlink/?LinkID=232441)   
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Přizpůsobení programového testu UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)   
 [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



