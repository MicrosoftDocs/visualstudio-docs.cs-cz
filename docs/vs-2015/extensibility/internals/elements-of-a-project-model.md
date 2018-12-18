---
title: Prvky modelu projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 818e58af478b3c86c4d0ce9daa9c439681de999e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810361"
---
# <a name="elements-of-a-project-model"></a>Prvky modelu projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozhraní a implementace všech projektů v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sdílet základní struktura: modelu projektu pro váš typ projektu. V modelu projektu, který je sady VSPackage, kterou vyvíjíte, můžete vytvořit objekty, které splňují vaše rozhodnutí o návrhu a fungují společně s globální funkce poskytované službou integrovaného vývojového prostředí. I když můžete řídit, jak je trvalý položku projektu, například můžete neovládají oznámení, že soubor musí nastavit jako trvalý. Když uživatel umístí fokus na otevřeném projektu položku a vybere **Uložit** na **souboru** nabídce [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nabídky panelu, musí kód typu projektu zachytit příkazu v prostředí IDE, zachovat souboru, a odesílat oznámení zpět do integrovaného vývojového prostředí, že soubor je již změnit.  
  
 Vaše VSPackage komunikuje s integrovaným vývojovým prostředím prostřednictvím služeb, které poskytují přístup k rozhraní IDE. Prostřednictvím určitých služeb, monitorování a trasy například příkazy a poskytují kontextové informace pro výběrech v projektu. Všechny globální funkce integrovaného vývojového prostředí potřebné pro vaše VSPackage poskytuje služby. Další informace o službách najdete v tématu [postupy: získání služby](../../extensibility/how-to-get-a-service.md).  
  
 Další důležité informace o implementaci:  
  
- Model jeden projekt může obsahovat více než jeden typ projektu.  
  
- Typy projektů a odebrání dodatečné projektu továren jsou registrovány nezávisle na sobě identifikátory GUID.  
  
- Soubor šablony nebo Průvodce inicializovat nový soubor projektu, když uživatel vytvoří nový projekt přes musí mít každý projekt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uživatelského rozhraní. Například [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] šablony inicializovat, co se nakonec stanou soubory .vcproj.  
  
  Následující obrázek znázorňuje primární rozhraní, služby a objekty, které tvoří implementaci obvyklou pro projekty. Aplikace pomocné rutiny, HierUtil7, můžete použít k vytvoření základní objektů a ostatní programovací často používaný text. Další informace o pomocné rutiny HierUtil7 aplikace najdete v tématu [není v sestavení: použití třídy HierUtil7 projektu k implementaci typu projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Visual Studio projekt modelu grafika](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  model projektu  
  
  Další informace o rozhraní a služby uvedené v předchozím diagramu a další volitelné rozhraní není zahrnuta v diagramu najdete v tématu [základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md).  
  
  Projekty mohou podporovat příkazy a proto musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní k účasti v příkazu směrování přes příkaz kontextu identifikátory GUID.  
  
## <a name="see-also"></a>Viz také  
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Není v sestavení: použití HierUtil7 projektu třídy k implementaci typu projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)   
 [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Postupy: získání služby](../../extensibility/how-to-get-a-service.md)   
 [Vytváření typů projektů](../../extensibility/internals/creating-project-types.md)

