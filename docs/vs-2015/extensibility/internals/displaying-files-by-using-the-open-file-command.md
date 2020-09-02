---
title: Zobrazení souborů pomocí příkazu otevřít soubor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd0018df4efb023357e10ab8050f6cf5e9eba1fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64826155"
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Zobrazení souborů pomocí příkazu Otevřít soubor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující postup popisuje, jak rozhraní IDE zpracovává příkaz pro **otevření souboru** , který je k dispozici v nabídce **soubor** v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Kroky také popisují, jak by projekty měly reagovat na volání, která pocházejí z tohoto příkazu.  
  
 Když uživatel klikne na příkaz **otevřít soubor** v nabídce **soubor** a vybere soubor v dialogovém okně **otevřít soubor** , dojde k následujícímu procesu.  
  
1. Pomocí tabulky běžícího dokumentu rozhraní IDE určí, zda je soubor již otevřen v projektu.  
  
    - Je-li soubor otevřen, rozhraní IDE ho překliká do okna.  
  
    - Pokud soubor není otevřen, rozhraní IDE zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> dotaz na každý projekt a určí, který projekt může soubor otevřít.  
  
        > [!NOTE]
        > V implementaci projektu pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Zadejte hodnotu priority, která určuje úroveň, na které váš projekt otevře soubor. Hodnoty priority jsou k dispozici ve <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> výčtu.  
  
2. Každý projekt reaguje na úroveň priority, která označuje důležitost, na kterou se má projekt otevřít, aby se soubor otevřel.  
  
3. Rozhraní IDE používá následující kritéria k určení, který projekt otevře soubor:  
  
    - Projekt, který reaguje s nejvyšší prioritou (DP_Intrinsic), otevře soubor. Pokud s touto prioritou bude reagovat více než jeden projekt, otevře se v prvním projektu odpověď.  
  
    - Pokud žádný projekt neodpoví nejvyšší prioritou (DP_Intrinsic), ale všechny projekty reagují se stejnou a nižší prioritou, otevře se soubor aktivní projekt. Pokud není aktivní žádný projekt, otevře se soubor s prvním projektem, který reaguje.  
  
    - Pokud žádný projekt neobsahuje vlastnictví souboru (DP_Unsupported), otevře se soubor s různými soubory.  
  
         Pokud je vytvořena instance projektu různé soubory, projekt vždy odpoví hodnotou DP_CanAddAsExternal. Tato hodnota označuje, že projekt může otevřít soubor. Tento projekt slouží k ustájení otevřených souborů, které nejsou v žádném jiném projektu. Seznam položek v tomto projektu není trvalý. Tento projekt je viditelný v **Průzkumník řešení** pouze v případě, že se používá k otevření souboru.  
  
         Pokud projekt různé soubory neindikuje, že může soubor otevřít, instance projektu nebyla vytvořena. V tomto případě rozhraní IDE vytvoří instanci projektu různé soubory a sdělí projektu, aby otevřel soubor.  
  
4. Jakmile rozhraní IDE určí, který projekt otevře soubor, zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodu v tomto projektu.  
  
5. Projekt pak má možnost otevřít soubor pomocí editoru specifického pro projekt nebo standardního editoru. Další informace najdete v tématu [Postup: otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md) a [Postup: otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení souborů pomocí příkazu otevřít v programu](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Otevírání a ukládání položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Postupy: otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md)   
 [Postupy: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)
