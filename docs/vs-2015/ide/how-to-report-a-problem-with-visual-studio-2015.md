---
title: Postup ohlášení problému se sadou Visual Studio 2015 | Dokumentace Microsoftu
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 24ecb76e-b7ad-432d-88ab-d9849963465d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 26758c63bb1de64c9497b67afc3f55b73238d5e4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064057"
---
# <a name="how-to-report-a-problem-with-visual-studio-2015"></a>Postup ohlášení problému se sadou Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci pro sadu Visual Studio 2017 najdete v tématu [jak chcete nahlásit problém v sadě Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

Pokud dojde k potížím s Visual Studiem 2015, chceme znát, takže jsme diagnostikovat a opravit ho.  S použitím **nahlásit problém** nástroj, můžete shromažďovat podrobné informace o problému a odesílají je společnosti Microsoft s několika málo kliknutí na tlačítko.

 Microsoft respektuje vaše soukromí. Informace o tom, jak jsme zacházet s daty, které nám pošlete, naleznete v tématu [prohlášení společnosti Microsoft Visual Studio Product řady](https://www.visualstudio.com/en-us/dn948229).

## <a name="open-the-report-a-problem-tool"></a>Otevřete sestavu nástroj problému
 Klikněte na ikonu zpětné vazby uživatelů vedle **Snadné spuštění** v záhlaví okna, nebo klikněte na **pomáhají &#124; odeslat zpětnou vazbu &#124; nahlásit problém**.

 ![Nahlásit problém položky nabídky](../ide/media/report-a-problem-menu-item.png "nahlásit problém položky nabídky")

## <a name="describe-the-problem"></a>Popište problém

###  <a name="describe_the_problem"></a>

1. Zadejte popisný název problému, pomůže nám to směrovat správnému týmu sady Visual Studio.

2. Zadejte další podrobnosti a pokud je to možné, kroky pro reprodukci problému.

3. Z rozevíracího seznamu zvolte problémové oblasti. Pokud si nejste jisti, proveďte co nejlepší odhad.

   ![Nahlásit problém dialogové okno](../ide/media/report-a-problem-dialog.png "nahlásit problém dialogové okno")

## <a name="provide-a-screenshot-optional"></a>Zadejte snímek obrazovky (volitelné)
 Zvolte **zahrnout snímek obrazovky** k odeslání společnosti Microsoft aktuální obrazovky. Nástroj umožňuje Oříznout okraje obrázku, chcete-li zobrazit pouze část obrazovky, který zobrazuje problém. Kliknutím můžete připojit další snímky obrazovky nebo jiné soubory **připojit další soubory** tlačítko.

## <a name="provide-a-trace-and-heap-dump-optional"></a>Zadejte trasování a haldy výpis (volitelné)

###  <a name="provide_a_trace_and_heap_dump"></a>

1.  Je nám s diagnostikou problémů velmi pomohou trasování a haldy soubory s výpisem paměti.   Děkujeme za to moc použijete sestavu problém nástroj pro záznam postupu k reprodukci a odesílala data do Microsoftu.

2.  Klikněte na dvojitou šipku vedle **zaznamenejte své akce pro reprodukci problému**. Pokud váš problém způsobují to, že sada Visual Studio přestane reagovat nebo havárií, pak otevře další instanci sady Visual Studio a vyberte ho ze zobrazení seznamu.

3.  Klikněte na **spustit záznam** a postupujte podle kroků, které problém reprodukovat. Jakmile budete hotovi, klikněte na **zastavit záznam** tlačítka v okně s plovoucí desetinnou čárkou.

4.  Počkejte několik minut, než Visual Studio se shromažďovat a balit informací, která byla zaznamenána. Dialogové okno bude vypadat asi takhle nějak. Po dokončení procesu shromažďování:

     ![Záznam trasování souboru](../ide/media/record-a-trace-file.png "záznam souboru trasování")

## <a name="describe-the-workaround-if-there-is-one"></a>Popište alternativní řešení, pokud existuje
 Pokud jste mohli problém vyřešit, popište prosím řešením pro pole pro úpravy pro tento účel k dispozici. To pomáhá nám nejen a Diagnostikujte problém, ale také jako pomoc dalším uživatelům, kteří mohou nastat stejný problém.

## <a name="submit-the-report"></a>Odeslat sestavu
 Klikněte na tlačítko pro odeslání k odeslání zprávy, spolu s všechny Image a soubory trasování nebo s výpisem paměti. Pokud **odeslat** tlačítko nejde aktivovat, ujistěte se, že jste zadali název a popis.

## <a name="see-also"></a>Viz také
 [Kontaktujte nás](../ide/talk-to-us.md)
