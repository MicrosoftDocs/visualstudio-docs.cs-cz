---
title: Analýza pokrytí kódu v testech pro ověření sestavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2442bf4cc31eeb51332aa28325924e18ccb1ffb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660719"
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analýza pokrytí kódu v testech pro ověření sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analýza pokrytí kódu v Microsoft Visual Studio ukazuje, jak velká část kódu je vykonávána automatizovanými testy. Další informace naleznete v tématu [Použití pokrytí kódu k určení, kolik kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

 Při vrácení kódu se změnami jsou testy spuštěny na serveru sestavení společně se všemi dalšími testy ostatních členů týmu. (Pokud jste to ještě neudělali, přečtěte si téma [spuštění testů v procesu sestavení](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) Je vhodné analyzovat pokrytí kódu ve službě sestavení, protože poskytuje nejaktuálnější a ucelený přehled o pokrytí v celém projektu. Takový postup bude také zahrnovat automatizované systémové testy a další kódované testy, které nejsou obvykle spouštěny na počítačích vývojářů.

1. V Team Explorer otevřete **sestavení**a pak přidejte nebo upravte definici sestavení.

2. Na stránce **proces** rozbalte položku **automatizované testy**, **zdroj testu**, **parametry spuštění**. Nastavte **typ souboru parametrů běhu** na možnost **pokrytí kódu povoleno**.

    Pokud máte více než jednu definici Zdroje testu, opakujte tento krok pro každou z nich.

   - <em>Ale k dispozici není žádné pole s názvem **typ souboru parametrů běhu</em>* . *

      V části **automatizované testy**vyberte možnost **test sestavení** a zvolte tlačítko se třemi tečkami **[...]** na konci řádku. V dialogovém okně **Přidat/upravit testovací běh** vyberte v části **Test Runner**možnost **Visual Studio Test Runner**.

   ![Nastavení definice sestavení pro pokrytí kódu](../test/media/codecoverage-plaincc.png "CodeCoverage – plainCC")

   Po spuštění sestavení se výsledky pokrytí kódu zobrazí v souhrnu sestavení.

## <a name="see-also"></a>Viz také
 [Použití pokrytí kódu k určení rozsahu testovaného kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
