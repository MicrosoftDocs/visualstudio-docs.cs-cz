---
title: Prvky modelu projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3b07068939e34b5c9e9487761177c0e12f5654
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700121"
---
# <a name="elements-of-a-project-model"></a>Prvky modelu projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozhraní a implementace všech projektů v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rámci sdílí základní strukturu: projektový model pro typ projektu. V modelu projektu, který je VSPackage, který vyvíjíte, vytváříte objekty, které vyhovují vašim rozhodnutím o návrhu a pracují společně s globálními funkcemi poskytovanými IDE. I když máte kontrolu nad tím, jak je položka projektu trvalá, například neřídíte oznámení, že soubor musí být trvalý. Když uživatel umístí fokus na otevřenou položku projektu a klikne na tlačítko **Uložit** v nabídce **soubor** na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] řádku nabídek, kód typu projektu musí zachytit příkaz z integrovaného vývojového prostředí, zachovat soubor a odeslat oznámení zpět do integrovaného vývojového prostředí, že soubor již není změněn.  
  
 Vaše VSPackage komunikuje s IDE prostřednictvím služeb, které poskytují přístup k rozhraním IDE. Například přes konkrétní služby můžete monitorovat a směrovat příkazy a poskytnout kontextové informace pro výběry provedené v projektu. Všechny globální funkce IDE, které jsou potřebné pro VSPackage, jsou poskytovány službami. Další informace o službách najdete v tématu [How to: get a Service](../../extensibility/how-to-get-a-service.md).  
  
 Další pokyny k implementaci:  
  
- Jeden model projektu může obsahovat více než jeden typ projektu.  
  
- Typy projektů a propracované továrny projektu jsou registrovány nezávisle s identifikátory GUID.  
  
- Každý projekt musí mít soubor šablony nebo průvodce pro inicializaci nového souboru projektu, když uživatel vytvoří nový projekt prostřednictvím [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uživatelského rozhraní. Například [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] šablony inicializují, co nakonec se stanou soubory. vcproj.  
  
  Následující ilustrace znázorňuje primární rozhraní, služby a objekty, které tvoří typickou implementaci projektu. K vytvoření základních objektů a dalších často používaných programovacích programů můžete použít pomocníka aplikace HierUtil7. Další informace o Pomocníkovi aplikace HierUtil7 naleznete v tématu [Not in Build: using HierUtil7 Project Classes pro implementaci typu projektu (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Obrázek modelu projektu sady Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  model projektu  
  
  Další informace o rozhraních a službách uvedených v předchozím diagramu a dalších volitelných rozhraních, která nejsou součástí diagramu, najdete v tématu [základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md).  
  
  Projekty mohou podporovat příkazy, a proto musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní pro účast v směrování příkazů prostřednictvím identifikátorů GUID kontextu příkazu.  
  
## <a name="see-also"></a>Viz také  
 [Kontrolní seznam: vytváření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Není v sestavení: použití tříd projektu HierUtil7 k implementaci typu projektu (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)   
 [Vytváření instancí projektu pomocí Továrnování projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Postupy: získání služby](../../extensibility/how-to-get-a-service.md)   
 [Vytváření typů projektů](../../extensibility/internals/creating-project-types.md)
