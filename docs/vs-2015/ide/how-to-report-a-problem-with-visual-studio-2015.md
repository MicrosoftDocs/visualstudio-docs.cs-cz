---
title: Nahlášení problému se sadou Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 24ecb76e-b7ad-432d-88ab-d9849963465d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e75215d2693b5fe2bf879c4b293ae853b42905e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651786"
---
# <a name="how-to-report-a-problem-with-visual-studio-2015"></a>Postup ohlášení problému se sadou Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [postup nahlášení problému v aplikaci Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

Pokud narazíte na problém se sadou Visual Studio 2015, chceme o něm znát, abychom ho mohli diagnostikovat a opravit.  Pomocí nástroje **nahlásit problém** můžete shromáždit podrobné informace o problému a odeslat ho společnosti Microsoft pomocí několika málo kliknutí na tlačítko.

Společnost Microsoft respektuje vaše soukromí. Informace o tom, jak se zachází s daty, která nám posíláte, najdete v tématu [Microsoft Visual Studio prohlášení o zásadách ochrany osobních údajů v rodině produktů](https://www.visualstudio.com/dn948229).

## <a name="open-the-report-a-problem-tool"></a>Otevřete nástroj nahlásit problém.

Klikněte na ikonu zpětné vazby uživatele v části **Snadné spuštění** v záhlaví nebo klikněte na **help > Odeslat názor > nahlásit problém**.

![Hlášení problému – položka nabídky](../ide/media/report-a-problem-menu-item.png "Hlášení problému – položka nabídky")

## <a name="describe-the-problem"></a>Popište problém.

### <a name="describe_the_problem"></a>

1. Poskytněte popisný název problému, který nám pomůže ho směrovat do správného týmu v rámci sady Visual Studio.

2. Uveďte další podrobnosti a pokud je to možné, kroky pro reprodukování problému.

3. Vyberte oblast problému z rozevíracího seznamu. Pokud si nejste jistí, proveďte co nejlépe odhad.

   ![Dialogové okno nahlásit problém](../ide/media/report-a-problem-dialog.png "Dialogové okno nahlásit problém")

## <a name="provide-a-screenshot-optional"></a>Zadejte snímek obrazovky (volitelné).

Chcete-li odeslat aktuální obrazovku společnosti Microsoft, vyberte možnost **Zahrnout snímek obrazovky** . Nástroj umožňuje oříznout obrázek, aby se zobrazila pouze část obrazovky, která zobrazuje problém. Kliknutím na tlačítko **připojit další soubory** můžete připojit další snímky obrazovky nebo jiné soubory.

## <a name="provide-a-trace-and-heap-dump-optional"></a>Poskytnutí trasování a výpisu haldy (volitelné)

### <a name="provide_a_trace_and_heap_dump"></a>

1. Trasování a soubory výpisu haldy jsou velmi užitečné při pomoci diagnostikovat problémy.   Oceňujeme, když použijete nástroj ohlásit problém k zaznamenání reprodukci kroků a odešlete data do Microsoftu.

2. Klikněte na dvojitou šipku vedle **položky zaznamenat vaše akce a problém reprodukován**. Pokud váš problém způsobuje, že aplikace Visual Studio přestane reagovat nebo dojde k chybě, otevřete jinou instanci aplikace Visual Studio a vyberte ji ze zobrazení seznamu.

3. Klikněte na **Start Record (Spustit záznam** ) a proveďte kroky, které reprodukovaly problém. Až skončíte, klikněte na tlačítko **Zastavit záznam** v plovoucím okně.

4. Počkejte několik minut, než sada Visual Studio shromáždí a zabalí informace, které se zaznamenaly. Po dokončení procesu shromažďování bude dialog vypadat přibližně takto:

     ![Zaznamenání trasovacího souboru](../ide/media/record-a-trace-file.png "Zaznamenání trasovacího souboru")

## <a name="describe-the-workaround-if-there-is-one"></a>Popište alternativní řešení, pokud existuje.

Pokud jste se mohli tomuto problému vyhnout, popište prosím alternativní řešení v poli pro úpravy, které je pro tento účel k dispozici. To nám pomáhá nejen diagnostikovat problém, ale také pomáhat ostatním uživatelům, kteří mohou narazit na stejný problém.

## <a name="submit-the-report"></a>Odeslat sestavu

Kliknutím na tlačítko Odeslat odešlete sestavu společně se všemi obrázky a soubory trasování nebo výpisu paměti. Pokud je tlačítko **Odeslat** zobrazeno šedě, ujistěte se, že jste zadali název a popis.

## <a name="see-also"></a>Viz také

- [Kontaktujte nás](../ide/talk-to-us.md)
