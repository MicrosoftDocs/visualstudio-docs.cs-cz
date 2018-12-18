---
title: Prvky modelu projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9eab0627184ac887aacfdfb2f275f0e8d9d30df7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912653"
---
# <a name="elements-of-a-project-model"></a>Prvky modelu projektu
Rozhraní a implementace všech projektů v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sdílet základní struktura: modelu projektu pro váš typ projektu. V modelu projektu, který je sady VSPackage, kterou vyvíjíte, můžete vytvořit objekty, které splňují vaše rozhodnutí o návrhu a fungují společně s globální funkce poskytované službou integrovaného vývojového prostředí. I když můžete řídit, jak je trvalý položku projektu, například můžete neovládají oznámení, že soubor musí nastavit jako trvalý. Když uživatel umístí fokus na otevřeném projektu položku a vybere **Uložit** na **souboru** nabídce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nabídky panelu, musí kód typu projektu zachytit příkazu v prostředí IDE, zachovat souboru, a odesílat oznámení zpět do integrovaného vývojového prostředí, že soubor je již změnit.  
  
 Vaše VSPackage komunikuje s integrovaným vývojovým prostředím prostřednictvím služeb, které poskytují přístup k rozhraní IDE. Prostřednictvím určitých služeb, monitorování a trasy například příkazy a poskytují kontextové informace pro výběrech v projektu. Všechny globální funkce integrovaného vývojového prostředí potřebné pro vaše VSPackage poskytuje služby. Další informace o službách najdete v tématu [postupy: získání služby](../../extensibility/how-to-get-a-service.md).  
  
 Další důležité informace o implementaci:  
  
- Model jeden projekt může obsahovat více než jeden typ projektu.  
  
- Typy projektů a odebrání dodatečné projektu továren jsou registrovány nezávisle na sobě identifikátory GUID.  
  
- Soubor šablony nebo Průvodce inicializovat nový soubor projektu, když uživatel vytvoří nový projekt přes musí mít každý projekt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní. Například [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] šablony inicializovat, co se nakonec stanou soubory .vcproj.  
  
  Následující obrázek znázorňuje primární rozhraní, služby a objekty, které tvoří implementaci obvyklou pro projekty. Můžete použít aplikaci pomocné rutiny, `HierUtil7`, chcete-li vytvořit objekty a ostatní programovací často používaný text. Další informace o `HierUtil7` pomocné rutiny aplikace, najdete v článku [HierUtil7 použití projektu třídy k implementaci typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Visual Studio projekt modelu grafika](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  model projektu  
  
  Další informace o rozhraní a služby uvedené v předchozím diagramu a další volitelné rozhraní není zahrnuta v diagramu najdete v tématu [základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md).  
  
  Projekty mohou podporovat příkazy a proto musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní k účasti v příkazu směrování přes příkaz kontextu identifikátory GUID.  
  
## <a name="see-also"></a>Viz také:  
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Použití HierUtil7 projektu třídy k implementaci typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)   
 [Vytvoření instance projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Postupy: získání služby](../../extensibility/how-to-get-a-service.md)   
 [Vytvořit typy projektů](../../extensibility/internals/creating-project-types.md)
