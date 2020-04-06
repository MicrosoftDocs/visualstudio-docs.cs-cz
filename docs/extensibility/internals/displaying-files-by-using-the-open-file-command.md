---
title: Zobrazení souborů pomocí příkazu Otevřít soubor | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708596"
---
# <a name="display-files-by-using-the-open-file-command"></a>Zobrazení souborů pomocí příkazu Otevřít soubor
Následující kroky popisují, jak rozhraní IDE zpracovává příkaz **Otevřít soubor,** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]který je k dispozici v nabídce **Soubor** v . Kroky také popisují, jak by měly projekty reagovat na volání, která pocházejí z tohoto příkazu.

 Když uživatel klepne na příkaz **Otevřít soubor** v nabídce **Soubor** a vybere soubor z dialogového okna **Otevřít soubor,** dojde k následujícímu procesu:

1. Pomocí spuštěné tabulky dokumentů ide určuje, zda je soubor již otevřen v projektu.

    - Pokud je soubor otevřený, rozhraní IDE znovu vyskakuje okno.

    - Pokud soubor není otevřen, IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> volá dotaz u každého projektu k určení, který projekt můžete otevřít soubor.

        > [!NOTE]
        > V implementaci projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>aplikace zadejte hodnotu priority, která označuje úroveň, na které projekt otevře soubor. Hodnoty priority jsou uvedeny ve výčtu. <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>

2. Každý projekt reaguje s úrovní priority, která označuje důležitost, kterou klade na projekt pro otevření souboru.

3. IDE používá následující kritéria k určení, který projekt otevře soubor:

    - Projekt, který odpoví s nejvyšší`DP_Intrinsic`prioritou ( ) otevře soubor. Pokud více než jeden projekt odpoví s touto prioritou, první projekt reagovat otevře soubor.

    - Pokud žádný projekt nereaguje s`DP_Intrinsic`nejvyšší prioritou ( ), ale všechny projekty reagují se stejnou, nižší prioritou, aktivní projekt otevře soubor. Pokud není aktivní žádný projekt, otevře soubor první projekt, na který bude reagovat.

    - Pokud žádný projekt nároky`DP_Unsupported`vlastnictví souboru ( ), různé soubory projektu otevře soubor.

         Pokud je vytvořena instance projektu Různé soubory, projekt vždy odpoví s hodnotou `DP_CanAddAsExternal`. Tato hodnota označuje, že projekt může soubor otevřít. Tento projekt se používá k domu otevřené soubory, které nejsou v žádném jiném projektu. Seznam položek v tomto projektu není trvalý. Tento projekt je viditelný v **Průzkumníku řešení** pouze v případě, že se používá k otevření souboru.

         Pokud projekt Různé soubory neznamená, že může soubor otevřít, nebyla vytvořena instance projektu. V tomto případě ide vytvoří instanci projektu Různé soubory a řekne projektu otevřít soubor.

4. Jakmile ide určuje, který projekt otevře soubor, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> volá metodu v tomto projektu.

5. Projekt pak má možnost otevření souboru pomocí editoru specifického pro projekt nebo standardní editor. Další informace naleznete v [tématu How to: Open project-specific editors](../../extensibility/how-to-open-project-specific-editors.md) and [How to: Open standard editors](../../extensibility/how-to-open-standard-editors.md), respectiverespective

## <a name="see-also"></a>Viz také
- [Zobrazení souborů pomocí příkazu Otevřít pomocí](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Postup: Otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md)
- [Postup: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)
