---
title: Výběr objektů kontextu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e1a43997d56f8d89f194fb83d20c1f160378873
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187428"
---
# <a name="selection-context-objects"></a>Kontextové objekty výběru
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Integrované vývojové prostředí (IDE) používá objekt kontextu globálního výběru k určení toho, co by mělo být zobrazeno v integrovaném vývojovém prostředí. Každé okno v integrovaném vývojovém prostředí může mít svůj vlastní objekt kontextu výběru, který je vložen do kontextu globálního výběru. Rozhraní IDE aktualizuje kontext globálního výběru hodnotami z okna, když má toto okno fokus. Další informace najdete v tématu [zpětné vazby pro uživatele](../../extensibility/internals/feedback-to-the-user.md).  
  
 Každý rámec okna nebo web v integrovaném vývojovém prostředí má službu s názvem <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Objekt vytvořený pomocí sady VSPackage, která je umístěná v rámci okna, musí volat `QueryService` metodu, aby získal ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> rozhraní.  
  
 Okna s rámečkem mohou uchovávat části jejich kontextu výběru z rozšiřování do globálního kontextu výběru při jejich spuštění. Tato možnost je užitečná pro okna nástrojů, která by mohla být začínat prázdným výběrem.  
  
 Změnou kontextu globálního výběru se aktivují události, které mohou rozhraní VSPackage monitorovat. Sady VSPackage mohou provádět následující úlohy implementací `IVsTrackSelectionEx` rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> :  
  
- Aktualizuje aktuálně aktivní soubor v hierarchii.  
  
- Monitorujte změny určitých typů prvků. Pokud například vaše VSPackage používá speciální okno **vlastností** , můžete sledovat změny v okně aktivních **vlastností** a v případě potřeby restartovat.  
  
  V následující posloupnosti se zobrazuje typický kurz sledování výběru.  
  
1. Rozhraní IDE načte kontext výběru z nově otevřeného okna a vloží ho do kontextu globálního výběru. Pokud kontext výběru používá HIERARCHY_DONTPROPAGATE nebo SELCONTAINER_DONTPROPAGATE, nejsou tyto informace šířeny do globálního kontextu. Další informace najdete v tématu [zpětné vazby pro uživatele](../../extensibility/internals/feedback-to-the-user.md).  
  
2. Události oznámení jsou vysílány do libovolného VSPackage, který je požadoval.  
  
3. Rozhraní VSPackage funguje na událostech, které obdrží, a to prováděním aktivit, jako je aktualizace hierarchie, opětovná aktivace nástroje nebo jiné podobné úlohy.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarchie v aplikaci Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Výběr a měna v integrovaném vývojovém prostředí](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Typy projektů](../../extensibility/internals/project-types.md)
