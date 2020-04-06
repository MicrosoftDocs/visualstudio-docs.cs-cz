---
title: Prvky modelu projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708528"
---
# <a name="elements-of-a-project-model"></a>Prvky modelu projektu
Rozhraní a implementace všech projektů [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v sdílet základní strukturu: model projektu pro typ projektu. V modelu projektu, což je VSPackage vyvíjíte, můžete vytvořit objekty, které jsou v souladu s rozhodnutími o návrhu a pracovat společně s globální funkce poskytované ide. I když řídíte, jak je položka projektu trvalé, například nemáte řízení oznámení, že soubor musí být trvalé. Když uživatel umístí fokus na otevřenou položku projektu a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vybere **uložit** do nabídky **Soubor** na panelu nabídek, musí kód typu projektu zachytit příkaz z rozhraní IDE, zachovat soubor a odeslat oznámení zpět do rozhraní IDE, že soubor již není změněn.

 Váš VSPackage spolupracuje s ide prostřednictvím služeb, které poskytují přístup k rozhraní IDE. Například prostřednictvím určitých služeb můžete sledovat a směrovat příkazy a poskytovat kontextové informace pro výběry provedené v projektu. Všechny globální funkce IDE potřebné pro váš VSPackage jsou poskytovány službami. Další informace o službách naleznete v [tématu How to: Get a service](../../extensibility/how-to-get-a-service.md).

 Další aspekty implementace:

- Jeden model projektu může obsahovat více než jeden typ projektu.

- Typy projektů a související továrny projektu jsou registrovány nezávisle na identifikátorech GUID.

- Každý projekt musí mít soubor šablony nebo průvodce pro inicializaci nového [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] souboru projektu, když uživatel vytvoří nový projekt prostřednictvím uživatelského rozhraní. Například [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] šablony inicializovat, co nakonec stane .vcproj soubory.

  Následující obrázek znázorňuje primární rozhraní, služby a objekty, které tvoří typické implementace projektu. Pomocník aplikace , `HierUtil7`můžete vytvořit základní objekty a další programovací text. Další informace o `HierUtil7` pomocníkovi aplikace naleznete v [tématu Použití tříd projektu HierUtil7 k implementaci typu projektu (C++).](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)

  ![Obrázek modelu projektu visual studia](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Model projektu

  Další informace o rozhraních a službách uvedených v předchozím diagramu a dalších volitelných rozhraních, která nejsou součástí diagramu, naleznete v [tématu Součásti jádra modelu aplikace Project](../../extensibility/internals/project-model-core-components.md).

  Projekty mohou podporovat příkazy <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> a proto musí implementovat rozhraní k účasti na směrování příkazů prostřednictvím identifikátorů GUID kontextu příkazu.

## <a name="see-also"></a>Viz také
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Použití tříd projektu HierUtil7 k implementaci typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Základní součásti modelu projektu](../../extensibility/internals/project-model-core-components.md)
- [Vytvoření instancí projektu pomocí továren projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Postup: Získání služby](../../extensibility/how-to-get-a-service.md)
- [Vytvořit typy projektů](../../extensibility/internals/creating-project-types.md)
