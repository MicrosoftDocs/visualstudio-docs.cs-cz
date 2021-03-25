---
title: Zobrazení souborů pomocí příkazu otevřít soubor | Microsoft Docs
description: Přečtěte si, jak integrované vývojové prostředí (IDE) sady Visual Studio zpracovává příkaz otevřít soubor v nabídce soubor pro zobrazení souborů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b2617050ff26536df5a94d0cb51fe74d37a55725
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061339"
---
# <a name="display-files-by-using-the-open-file-command"></a>Zobrazení souborů pomocí příkazu otevřít soubor
Následující postup popisuje, jak rozhraní IDE zpracovává příkaz pro **otevření souboru** , který je k dispozici v nabídce **soubor** v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Kroky také popisují, jak by projekty měly reagovat na volání, která pocházejí z tohoto příkazu.

 Když uživatel klikne na příkaz **otevřít soubor** v nabídce **soubor** a vybere soubor v dialogovém okně **otevřít soubor** , dojde k následujícímu procesu:

1. Pomocí tabulky běžícího dokumentu rozhraní IDE určí, zda je soubor již otevřen v projektu.

    - Je-li soubor otevřen, rozhraní IDE ho překliká do okna.

    - Pokud soubor není otevřen, rozhraní IDE zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> dotaz na každý projekt a určí, který projekt může soubor otevřít.

        > [!NOTE]
        > V implementaci projektu pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Zadejte hodnotu priority, která určuje úroveň, na které váš projekt otevře soubor. Hodnoty priority jsou k dispozici ve <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> výčtu.

2. Každý projekt reaguje na úroveň priority, která označuje důležitost, na kterou se má projekt otevřít, aby se soubor otevřel.

3. Rozhraní IDE používá následující kritéria k určení, který projekt otevře soubor:

    - Projekt, který reaguje s nejvyšší prioritou ( `DP_Intrinsic` ), otevře soubor. Pokud s touto prioritou bude reagovat více než jeden projekt, otevře se v prvním projektu odpověď.

    - Pokud žádný projekt neodpoví nejvyšší prioritou ( `DP_Intrinsic` ), ale všechny projekty reagují se stejnou a nižší prioritou, otevře se soubor aktivní projekt. Pokud není aktivní žádný projekt, otevře se soubor s prvním projektem, který reaguje.

    - Pokud žádný projekt neškodí vlastnictví souboru ( `DP_Unsupported` ), soubor s různými soubory se otevře.

         Pokud je vytvořena instance projektu různé soubory, projekt vždy odpoví hodnotou `DP_CanAddAsExternal` . Tato hodnota označuje, že projekt může otevřít soubor. Tento projekt slouží k ustájení otevřených souborů, které nejsou v žádném jiném projektu. Seznam položek v tomto projektu není trvalý. Tento projekt je viditelný v **Průzkumník řešení** pouze v případě, že se používá k otevření souboru.

         Pokud projekt různé soubory neindikuje, že může soubor otevřít, instance projektu nebyla vytvořena. V tomto případě rozhraní IDE vytvoří instanci projektu různé soubory a sdělí projektu, aby otevřel soubor.

4. Jakmile rozhraní IDE určí, který projekt otevře soubor, zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodu v tomto projektu.

5. Projekt pak má možnost otevřít soubor pomocí editoru specifického pro projekt nebo standardního editoru. Další informace najdete v tématu [Postup: otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md) a [Postup: otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)v uvedeném pořadí.

## <a name="see-also"></a>Viz také
- [Zobrazení souborů pomocí příkazu otevřít v programu](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Otevřít a uložit položky projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Postupy: otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md)
- [Postupy: otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)
