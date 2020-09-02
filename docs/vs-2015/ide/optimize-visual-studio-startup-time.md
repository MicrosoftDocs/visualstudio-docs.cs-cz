---
title: Optimalizovat čas spuštění | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f00bbc7741768852b5928b249dc7035bc440992
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670404"
---
# <a name="optimize-visual-studio-startup-time"></a>Optimalizace spouštění sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V ideálním případě by se měla aplikace Visual Studio vždy spouštět co nejrychleji. Rozšíření sady Visual Studio a otevřená okna nástrojů ale můžou negativně ovlivnit čas spuštění, protože se při spuštění automaticky načítají. Okno **spravovat výkon sady Visual Studio** umožňuje nejen zobrazit, která rozšíření a funkce ovlivňují čas spuštění sady Visual Studio, ale také umožňuje určit jejich chování při načítání, abyste měli větší kontrolu nad tím, jak rychle se spustí Visual Studio.

## <a name="control-startup-behavior"></a>Řízení chování při spuštění

Aby nedošlo k prodloužení doby spuštění, aplikace Visual Studio 2017 a novější nenačítá rozšíření během spouštění pomocí přístupu na vyžádání. To znamená, že rozšíření se neotevřou hned po spuštění sady Visual Studio, ale místo toho se spustí asynchronně podle potřeby po spuštění. Vzhledem k tomu, že okna nástrojů, která zůstala otevřená v předchozí relaci sady Visual Studio, mohou také zpomalit spuštění, Visual Studio otevírá okna nástrojů inteligentním způsobem, aby se předešlo neovlivnění času spuštění.

Pokud aplikace Visual Studio zjistí pomalé spuštění, zobrazí se automaticky otevíraná okna upozorňující na rozšíření nebo panel nástrojů, který způsobuje zpomalení. Zpráva také obsahuje odkaz na dialogové okno **spravovat výkon sady Visual Studio** , ve kterém jsou uvedena okna rozšíření a nástroje, která mají vliv na výkon při spuštění. Toto dialogové okno umožňuje změnit nastavení rozšíření a panelu nástrojů, aby se zlepšil výkon při spuštění.

![Spravovat výkon sady Visual Studio – místní nabídka](../ide/media/vside-perfdialog-popup.PNG "Spravovat výkon sady Visual Studio – místní nabídka")

Dialogové okno **spravovat výkon sady Visual Studio** má dvě kategorie: **rozšíření** a **okna nástrojů**.

### <a name="control-extensions"></a>Rozšíření ovládacích prvků
Pokud rozšíření zpomaluje spuštění sady Visual Studio, toto rozšíření se zobrazí v **dialogovém okně Spravovat výkon sady Visual Studio** , když vyberete jeden z typů rozšíření. Pokud je dopad na dobu spuštění (uvedený v části **dopad** ) nepřijatelný, můžete zvolit možnost při spuštění vždy zakázat rozšíření výběrem tlačítka **Zakázat** . Můžete znovu povolit rozšíření pro budoucí relace pomocí Správce rozšíření nebo dialogového okna spravovat výkon sady Visual Studio.

![Správa výkonu sady Visual Studio – rozšíření](../ide/media/vside-perfdialog-extensions.PNG "Správa výkonu sady Visual Studio – rozšíření")

Kromě spouštěcích rozšíření můžete také zakázat rozšíření, která se načítají při načítání řešení nebo když uživatel zadá typ. Chcete-li zobrazit seznam přidružených rozšíření, stačí zvolit scénář.

### <a name="control-tool-windows"></a>Okna řídicích nástrojů
Pokud okno nástroje zpomaluje spuštění sady Visual Studio, můžete ho ponechat ve výchozím chování (neposkytujete žádné výhody při spuštění) nebo můžete přepsat jeho chování tak, že vyberete jedno ze dvou chování:

- **Nezobrazovat okno při spuštění:** Zvolíte-li tuto možnost, bude zadané okno nástroje vždy zavřeno při otevření sady Visual Studio, a to i v případě, že zůstane otevřeno v předchozí relaci. Z nabídky můžete otevřít okno nástrojů.
- **Automaticky skrýt okno při spuštění:** Pokud bylo okno nástroje ponecháno otevřené v předchozí relaci, volba této možnosti sbalí skupinu okna nástroje při spuštění, aby nedošlo k inicializaci okna nástroje. Tato možnost je vhodná, pokud používáte okno nástroje často, protože okno nástroje je stále k dispozici, ale již nemá negativní vliv na dobu spuštění sady Visual Studio.

![Správa výkonu sady Visual Studio – okna nástrojů](../ide/media/vside-perfdialog-toolwindows.PNG "Správa výkonu sady Visual Studio – okna nástrojů")

Pokud později změníte svůj názor, můžete vrátit některou z těchto možností v dialogovém okně **spravovat výkon sady Visual Studio** . Chcete-li otevřít dialogové okno **spravovat výkon sady Visual Studio** , na panelu nabídek vyberte možnost **help**a **spravovat výkon sady Visual Studio**.
