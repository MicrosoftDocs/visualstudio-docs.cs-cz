---
title: Vytvoření offline instalace
description: Zjistěte, jak v režimu offline instalace sady Visual Studio, když máte nespolehlivým připojení k Internetu nebo s malou šířkou pásma.
ms.custom: seodec18
ms.date: 08/28/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37d218893ab16a8d0907e608ebeb3b02ab944385
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159981"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Vytvoření offline instalace sady Visual Studio 2017

Jsme navrhovali Visual Studio 2017, aby dobře fungovaly v různých konfiguracích sítě a počítače. Přestože doporučujeme vám vyzkoušet [webovou Instalační službu sady Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;což je malý soubor a umožňuje aktuální nejnovější opravy a funkce&mdash;rozumí tomu, že nemusí být možné.

Například může mít nespolehlivé připojení k Internetu nebo, pokud má s malou šířkou pásma. Pokud ano, máte několik možností: Můžete použít novou "Vše stáhnout, potom nainstalovat" funkcí ke stažení souborů, před instalací nebo příkazového řádku můžete vytvořit místní mezipaměť souborů.

> [!NOTE]
> Pokud jste správce organizace, který chce provést nasazení sady Visual Studio 2017 k síti klientských pracovních stanic, které jsou aplikována brána firewall z Internetu, najdete v našich [vytvoření síťové instalace sady Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) a [Instalaci certifikátů vyžadovaných pro offline instalace sady Visual Studio](../install/install-certificates-for-visual-studio-offline.md) stránky.

## <a name="use-the-download-all-then-install-feature"></a>Používá "vše stáhnout, potom nainstalovat" funkce

[**Novinka v 15.8**](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017#install
): Po stažení webovou Instalační službu vyberte novou **vše stáhnout, potom nainstalovat** možnost z instalačního programu sady Visual Studio. Pokračujte s instalací.

   !["Vše stáhnout, potom nainstalovat" možnost](media/download-all-then-install.png)

## <a name="use-the-command-line-to-create-a-local-cache"></a>Místní mezipaměť vytvořit pomocí příkazového řádku

Po stažení malé zaváděcí nástroj, použijte příkazový řádek k vytvoření místní mezipaměti. Potom použijte místní mezipaměti instalace sady Visual Studio. (Tento proces nahradí soubory ISO, které byly k dispozici pro předchozí verze).

Tady je způsob.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 – stažení zaváděcího nástroje Visual Studio

Musíte mít internetové připojení k dokončení tohoto kroku.

Začněte tím, že stažení zaváděcího nástroje Visual Studio pro vaši zvolenou edici sady Visual Studio. Váš soubor&mdash;nebo zaváděcí nástroj&mdash;bude odpovídat nebo se podobně jako na jednu z následujících akcí.

| Edice                    | Soubor                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

### <a name="step-2---create-a-local-install-cache"></a>Krok 2: vytvoření mezipaměti místní instalace

Musíte mít internetové připojení k dokončení tohoto kroku.

> [!IMPORTANT]
> Pokud nainstalujete Visual Studio Community 2017, musíte ji aktivovat do 30 dní od instalace. To vyžaduje připojení k Internetu.

Otevřete příkazový řádek a použijte jeden z příkazů z následujících příkladů. Příklady, které jsou zde uvedeny předpokládají, že používáte komunitní edice sady Visual Studio; Upravte příkaz v závislosti na edici.

- Vývoj desktopových aplikací .NET a webové rozhraní .NET spusťte:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- Vývoj pro Office a .NET desktop spusťte:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Vývoje desktopových aplikací C++ pro spuštění:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Vytvoření kompletní místní rozložení se všemi funkcemi (bude to trvat dlouho&mdash;máme _velké_ funkcí!), spusťte:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Pokud chcete nainstalovat jiný jazyk než angličtinu, změňte `en-US` národní prostředí z [seznam národních prostředí jazyka](#list-of-language-locales). Potom použijte [seznamu komponent a úlohy, které jsou k dispozici](workload-and-component-ids.md) můžete dále přizpůsobit vaše mezipaměť instalace.

> [!IMPORTANT]
> Úplné rozložení sady Visual Studio 2017 vyžaduje minimálně 35 GB místa na disku a může trvat nějakou dobu ke stažení. Zobrazit [použitím parametrů příkazového řádku instalace sady Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) informace o tom, jak vytvořit rozložení s pouze ty součásti, kterou chcete nainstalovat.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3: instalace sady Visual Studio z místní mezipaměti

> [!TIP]
> Při spuštění z mezipaměti místní instalace instalační program používal místní verze každý z těchto souborů. Ale pokud vyberete součásti během instalace, které nejsou v mezipaměti, instalační program se pokusí stáhnout z Internetu.

Chcete-li mít jistotu, že můžete nainstalovat pouze soubory, které jste předtím stáhli, použijte stejné možnosti příkazového řádku, které jste použili k vytvoření mezipaměti rozložení. Například, pokud jste vytvořili mezipaměť rozložení pomocí následujícího příkazu:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Spuštění instalace pak použijte tento příkaz:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Pokud dojde k chybě, podpis je neplatný, je nutné nainstalovat aktualizace certifikátů. Otevřete složku pro certifikáty v offline mezipaměti. Klikněte dvakrát na každém ze souborů certifikátu a klikněte na Průvodce správce certifikátů. Pokud budete vyzváni k zadání hesla, ponechte prázdné.

### <a name="list-of-language-locales"></a>Seznam národních prostředí jazyka

| **Jazyk národního prostředí** | **Jazyk** |
| ----------------------- | --------------- |
| cs-CZ | Čeština |
| de-DE | Němčina |
| en-US | Angličtina |
| es-ES | Španělština |
| fr-FR | Francouzština |
| IT-IT | Italština |
| ja-JP | Japonština |
| ko-KR | Korejština |
| pl-PL | Polština |
| pt-BR | Portugalština – Brazílie |
| ru-RU | Ruština |
| tr-TR | Turečtina |
| zh-CN | Čínština (zjednodušená) |
| zh-TW | Čínština (tradiční) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

- [Vytvoření síťové instalace sady Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md)
- [Instalace certifikátů vyžadovaných pro offline instalace sady Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
- [ID pracovního vytížení a komponenta Visual Studio 2017](workload-and-component-ids.md)
