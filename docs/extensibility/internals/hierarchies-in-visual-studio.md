---
title: Hierarchie v sadě Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708192"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchie v sadě Visual Studio
Integrované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vývojové prostředí (IDE) zobrazí projekt jako *hierarchii*. V rozhraní IDE je hierarchie stromu uzlů, kde každý uzel má sadu přidružených vlastností. *Hierarchie projektu* je kontejner, který obsahuje položky projektu, vztahy položek a přidružené vlastnosti a příkazy položek.

 V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aplikaci můžete spravovat hierarchie projektů <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>pomocí rozhraní hierarchie . Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> přesměruje příkazy, které vyvoláte z položek projektu, do příslušného okna hierarchie namísto standardní obslužné rutiny příkazu.

## <a name="project-hierarchies"></a>Hierarchie projektů
 Každá hierarchie projektu obsahuje položky, které můžete zobrazit a upravit. Tyto položky se liší v závislosti na typu projektu. Databázový projekt může například obsahovat uložené procedury, zobrazení databáze a databázové tabulky. Projekt programovacího jazyka, na druhé straně, bude pravděpodobně zahrnovat zdrojové soubory a soubory prostředků pro bitmapy a dialogová okna. Hierarchie mohou být vnořeny, což vám dává určitou větší flexibilitu při vytváření hierarchie projektu.

 Při vytváření nového typu projektu řídí typ projektu úplnou sadu položek, které lze v něm upravovat. Projekty však mohou obsahovat položky, pro které nemají podporu úprav. Například projekty Visual C++ mohou obsahovat soubory HTML, i když visual c++ neposkytuje žádný vlastní editor pro typ souboru HTML.

 Hierarchie spravují trvalost položek, které obsahují. Implementace hierarchie musí řídit všechny speciální vlastnosti, které ovlivňují trvalost položek v hierarchii. Například pokud položky představují objekty v úložišti namísto souborů, implementace hierarchie musí řídit trvalost těchto objektů. Ide sám řídí hierarchii uložit položky v souladu se vstupem uživatele, ale ide neřídí žádné akce potřebné k uložení těchto položek. Místo toho je projekt pod kontrolou.

 Když uživatel otevře položku v editoru, hierarchie, která řídí tuto položku, je vybrána a stane se aktivní hierarchií. Vybraná hierarchie určuje sadu příkazů, které jsou k dispozici pro činnost s položkou. Sledování zaměření uživatele tímto způsobem umožňuje hierarchii odrážet aktuální kontext uživatele.

## <a name="see-also"></a>Viz také
- [Typy projektů](../../extensibility/internals/project-types.md)
- [Výběr a měna v ide](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Vzorky VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
