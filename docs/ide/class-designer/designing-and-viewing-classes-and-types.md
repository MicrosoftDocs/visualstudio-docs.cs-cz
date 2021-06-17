---
title: Použít Návrhář tříd
description: Naučte se, jak navrhovat, vizualizovat a Refaktorovat třídy a další typy v kódu pomocí Návrhář tříd v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
- vs.classdesigner.enum
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85921343ac52c066735d607ce32635e953cf2e6a
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254784"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Návrh a zobrazení tříd a typů pomocí Návrhář tříd

Navrhněte, Vizualizujte a refaktorujte třídy a další typy v kódu pomocí **Návrhář tříd** v aplikaci Visual Studio. Pomocí diagramů tříd můžete vytvářet a upravovat třídy v projektu C#, Visual Basic nebo C++. Můžete také použít diagramy tříd pro lepší pochopení struktury projektu nebo reorganizace kódu.

>[!NOTE]
>Návrhář tříd není v projektech .NET Core k dispozici.

## <a name="what-you-can-do-with-class-diagrams"></a>Co můžete dělat s diagramy tříd

- **Návrh**: Upravte kód projektu úpravou diagramu tříd. Přidejte nové prvky a odstraňte nechtěné. Vaše změny se projeví v kódu.

- **Vizualizace**: pochopení struktury projektu zobrazením tříd v projektu v diagramu. Přizpůsobte si svůj diagram, abyste se mohli soustředit na podrobnosti o projektu, které se vám týkají nejvíc. Uložte diagram pro použití později k vyukázce nebo dokumentaci.

- **Refaktoring**: přepište metody, přejmenovat identifikátory, parametry refaktoru a implementujte rozhraní a abstraktní třídy.

## <a name="view-types-and-relationships"></a>Zobrazení typů a vztahů

Diagramy tříd zobrazují podrobnosti typů, například jejich členy prvků, a vztahy mezi nimi. Vizualizace těchto entit je dynamické zobrazení kódu. To znamená, že můžete upravit typy v návrháři a pak zobrazit vaše úpravy, které se projeví ve zdrojovém kódu entity. Podobně, diagram tříd je udržován v synchronizaci se změnami, které provedete v souborech kódu.

> [!NOTE]
> Pokud projekt obsahuje diagram tříd a váš projekt odkazuje na typ, který je umístěn v jiném projektu, diagram třídy nezobrazuje odkazovaný typ, dokud nevytvoříte projekt pro daný typ. Podobně Diagram nezobrazuje změny kódu externí entity, dokud projekt znovu sestavíte pro tuto entitu.

## <a name="class-diagram-workflow"></a>Pracovní postup diagramu tříd

Diagramy tříd vám mohou porozumět struktuře tříd projektů. Tyto projekty mohou být vytvořeny jinými vývojáři nebo potřebujete pouze aktualizační program pro projekt, který jste sami vytvořili. Diagramy tříd můžete použít k přizpůsobení, sdílení a prezentaci informací o projektu s ostatními.

Prvním krokem při prezentaci informací o projektu je vytvoření diagramu tříd, který zobrazuje, co chcete zobrazit. Další informace najdete v tématu [přidání diagramu tříd](how-to-add-class-diagrams-to-projects.md). Můžete vytvořit více diagramů tříd pro projekt, které lze použít k zobrazení odlišného zobrazení projektu, zvolené podmnožiny typů projektu nebo zvolené podmnožiny členů typů.

Kromě určení toho, jaký diagram tříd se zobrazuje, můžete také změnit způsob, jakým se informace zobrazují; Další informace naleznete v tématu [How to: Customizing Diagrams Class](how-to-customize-class-diagrams.md).

Po vyladění jednoho nebo více diagramů tříd je můžete zkopírovat do systém Microsoft Office dokumentů a vytisknout je, nebo je exportovat jako soubory obrázků. Další informace naleznete v tématu [Postupy: kopírování prvků diagramu tříd do dokumentu systém Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [Postupy: Tisk diagramů tříd](how-to-print-class-diagrams.md) a [Postupy: Export diagramů tříd jako obrázků](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Návrhář tříd nesleduje umístění zdrojových souborů, takže změna struktury projektu nebo přesunutí zdrojových souborů v projektu může způsobit, že Návrhář tříd ztratí záznam o typu, zejména zdrojový typ typu typedef, základní třídy nebo typy přidružení. Může se zobrazit chyba, například **Návrhář tříd není možné zobrazit tento typ**. Pokud tak učiníte, znovu přetáhněte změněný nebo znovu umístěný zdrojový kód do diagramu tříd a znovu ho zobrazte.

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../writing-code-in-the-code-and-text-editor.md)
- [Mapování závislostí napříč vaším řešením](../../modeling/map-dependencies-across-your-solutions.md)
