---
title: Použít Návrhář e-class
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c65be2b5afe91f9ee20a5eecde57d790a0cbcb2c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590394"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Návrh a zobrazení tříd a typů pomocí návrháře tříd

Navrhujte, vizualizujte a refaktorujte třídy a další typy v kódu pomocí **Návrháře tříd** v sadě Visual Studio. Diagramy tříd slouží k vytváření a úpravám tříd v projektu Jazyka C#, Visual Basic nebo C++. Diagramy tříd můžete také použít k lepšímu pochopení struktury projektu nebo k reorganizaci kódu.

## <a name="what-you-can-do-with-class-diagrams"></a>Co můžete dělat s diagramy tříd

- **Návrh**: Upravte kód projektu úpravou diagramu třídy. Přidejte nové prvky a odstraňte nežádoucí. Změny se projeví v kódu.

- **Vizualizujte**: Pochopte strukturu projektu zobrazením tříd v projektu v diagramu. Přizpůsobte si diagram tak, abyste se mohli soustředit na podrobnosti projektu, na kterých vám nejvíce záleží. Uložte diagram a použijte jej později pro předvádění nebo dokumentaci.

- **Refaktor :** Přepsat metody, přejmenovat identifikátory, refaktorovat parametry a implementovat rozhraní a abstraktní třídy.

## <a name="view-types-and-relationships"></a>Zobrazení typů a vztahů

Diagramy tříd zobrazují podrobnosti typů, například jejich základní členy a vztahy mezi nimi. Vizualizace těchto entit je dynamický pohled do kódu. To znamená, že můžete upravit typy v návrháři a pak vidět vaše úpravy se projeví ve zdrojovém kódu entity. Podobně diagram třídy je udržována v synchronizaci se změnami, které provedete v souborech kódu.

> [!NOTE]
> Pokud váš projekt obsahuje diagram třídy a projekt odkazuje na typ, který je umístěn v jiném projektu, diagram třídy nezobrazuje odkazovaný typ, dokud nevytvoříte projekt pro tento typ. Podobně diagram nezobrazuje změny kódu externí entity, dokud neobnovíte projekt pro tuto entitu.

## <a name="class-diagram-workflow"></a>Pracovní postup diagramu třídy

Diagramy tříd vám mohou pomoci pochopit strukturu tříd projektů. Tyto projekty mohly být vytvořeny jinými vývojáři nebo potřebujete pouze aktualizaci projektu, který jste sami vytvořili. Diagramy tříd můžete použít k přizpůsobení, sdílení a prezentaci informací o projektu s ostatními.

Prvním krokem při prezentaci informací o projektu je vytvoření diagramu třídy, který zobrazuje, co chcete zobrazit. Další informace naleznete [v tématu Přidání diagramu třídy](how-to-add-class-diagrams-to-projects.md). Můžete vytvořit více diagramů tříd pro projekt, který lze použít k zobrazení odlišné zobrazení projektu, vybranou podmnožinu typů projektu nebo vybranou podmnožinu členů typů.

Kromě definování toho, co jednotlivé diagramy třídy zobrazují, můžete také změnit způsob, jakým jsou informace prezentovány; Další informace naleznete v [tématu Postup: Přizpůsobení diagramů tříd](how-to-customize-class-diagrams.md).

Po vyladění jednoho nebo více diagramů tříd je můžete zkopírovat do dokumentů sady Microsoft Office a vytisknout je nebo je exportovat jako obrazové soubory. Další informace naleznete v [tématu Postup: Kopírování prvků diagramu třídy do dokumentu sady Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [Postup: Tisk diagramů tříd](how-to-print-class-diagrams.md) a [Postup: Export diagramů tříd jako obrázků](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Návrhář tříd nesleduje umístění zdrojových souborů, takže změna struktury projektu nebo přesunutí zdrojových souborů v projektu může způsobit, že Návrhář tříd ztratí přehled o typu, zejména zdrojový typ typedef, základní třídy nebo typy přidružení. Může se zobrazit chyba, jako **je návrhář tříd nemůže zobrazit tento typ**. Pokud tak učiníte, přetáhněte upravený nebo přemístěný zdrojový kód do diagramu třídy znovu zobrazit.

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../writing-code-in-the-code-and-text-editor.md)
- [Mapování závislostí napříč vaším řešením](../../modeling/map-dependencies-across-your-solutions.md)
