---
title: Hierarchie
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
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2373909dbf218f24f148e0601d4dbb39cff1868
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061898"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchie v sadě Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrované vývojové prostředí (IDE) se zobrazí jako projekt *hierarchie*. V integrovaném vývojovém prostředí hierarchie je strom z uzlů, kde má každý uzel sadu přidružené vlastnosti. A *projektu hierarchie* je kontejner, který obsahuje položky tohoto projektu, položek relací a přidružené vlastnosti položky a příkazy.

 V [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], Správa hierarchií projektu s použitím rozhraní hierarchie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Rozhraní přesměruje příkazů vyvoláte z položek projektu do okna příslušné hierarchii místo standardní příkaz obslužné rutiny.

## <a name="project-hierarchies"></a>Hierarchie projektu
 Každá hierarchie projektu obsahuje položky, které můžete zobrazit a upravit. Tyto položky se liší v závislosti na typu projektu. Například databázový projekt může obsahovat uložené procedury, zobrazení databáze a databázových tabulek. Programovací jazyk projektu, na druhé straně, bude pravděpodobně obsahovat zdrojové soubory a soubory prostředků pro rastrové obrázky a v dialogových oknech. Mohou být vnořené hierarchie, která poskytuje některé vyšší flexibilitu při vytváření hierarchie projektu.

 Když vytvoříte nový typ projektu, určuje typ projektu kompletní sadu položek, které lze upravovat v ní. Projekty však může obsahovat položky, pro které nemají podporu editaci. Například projekty Visual C++ může obsahovat soubory HTML, i když Visual C++ neposkytuje žádné vlastní editor pro tento typ souboru HTML.

 Hierarchie spravovat trvalost položky, které obsahují. Implementace v hierarchii musí řídit všechny speciální vlastnostmi, které ovlivňují trvalost položky v rámci hierarchie. Například pokud položky představují objektů v úložišti místo souborů, provádění hierarchie řídit trvalou dostupnost těchto objektů. Hierarchie, které chcete uložit položky uživatelský vstup v souladu s přesměruje samotném integrovaném vývojovém prostředí, ale rozhraní IDE neřídí všechny akce nezbytné k uložení těchto položek. Místo toho je projekt v ovládacím prvku.

 Když uživatel otevře položku v editoru, hierarchie, která určuje, že položka je vybraná a stane aktivní hierarchii. U vybrané hierarchie určuje sadu příkazů, které jsou dostupné tak, aby fungoval na položce. Sledování fokus uživatele tímto způsobem umožňuje hierarchie, aby odrážela aktuální kontextu uživatele.

## <a name="see-also"></a>Viz také
 [Typy projektů](../../extensibility/internals/project-types.md) [výběr a Měna v prostředí IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md) [VSSDK ukázky](../../misc/vssdk-samples.md)
