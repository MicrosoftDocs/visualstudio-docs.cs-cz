---
title: Kontextové objekty výběru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f09bcb260f4edd09045f860ed08d951622e54a5d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913160"
---
# <a name="selection-context-objects"></a>Kontextové objekty výběru
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrované vývojové prostředí (IDE) používá objekt kontextu globálního výběru k určení, co má být zobrazen v integrovaném vývojovém prostředí. Každé okno v integrovaném vývojovém prostředí může mít svůj vlastní objekt kontextu výběr do kontextu globálního výběru. Rozhraní IDE aktualizuje globální výběr kontextu s hodnotami z okna, když má okno fokus. Další informace najdete v tématu [zpětná vazba uživateli](../../extensibility/internals/feedback-to-the-user.md).  
  
 Každý rámeček okna nebo serveru v integrovaném vývojovém prostředí má služby zvané <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Objekt vytvořený pomocí vašeho balíčku VSPackage, která je umístěna v rámci okna musí volat `QueryService` metodu k získání ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> rozhraní.  
  
 Okna s rámečkem zachovat části informace o jejich výběr kontextu propagace v kontextu globálního výběru při spuštění. Tato možnost je užitečná pro panel nástrojů, které může být nutné začít s prázdnou výběru.  
  
 Úpravy globální výběr kontextu události, které můžete monitorovat balíčky VSPackages. Rozšíření VSPackages můžete provádět následující úlohy implementací `IVsTrackSelectionEx` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> rozhraní:  
  
- Aktualizace souboru aktuálně aktivní v hierarchii.  
  
- Monitorování se změní na určité typy prvků. Například, pokud vaše VSPackage používá speciální **vlastnosti** okna, můžete sledovat změny v aktivním **vlastnosti** okno a jenom v případě potřeby restartujte.  
  
  K následujícímu pořadí ukazuje typické kurzu výběr sledování.  
  
1.  Rozhraní IDE načte kontext výběru z nově otevřeném okně a umístí ji v rámci globálního výběru. Pokud výběr kontextu používá HIERARCHY_DONTPROPAGATE nebo SELCONTAINER_DONTPROPAGATE, tyto informace se nerozšíří do globální kontext. Další informace najdete v tématu [zpětná vazba uživateli](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Oznámení události vysílají jakékoli VSPackage, která je požadovaná.  
  
3.  Sady VSPackage funguje na události, které přijímá pomocí provádí aktivity, například aktualizace hierarchii opětovná aktivace nástroj nebo dalších podobných úloh.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Výběr a Měna v prostředí IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Typy projektů](../../extensibility/internals/project-types.md)