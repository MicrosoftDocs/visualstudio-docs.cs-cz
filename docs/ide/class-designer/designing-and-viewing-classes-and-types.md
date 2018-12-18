---
title: Použít Návrháře – třída
ms.date: 05/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4e4cf8e21f3f053783b1f7b70dcc51f2fd4ef2a
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447957"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Návrh a zobrazení tříd a typů pomocí návrháře tříd

Návrh, vizualizovat a Refaktorovat třídami a ostatními typy v kódu s **návrhář tříd** v sadě Visual Studio. Použití diagramů tříd můžete vytvářet a upravovat třídy ve vašem projektu C#, Visual Basic nebo C++. Můžete taky diagramy tříd pochopit strukturu projektu lepší nebo reorganizovat vašeho kódu.

## <a name="what-you-can-do-with-class-diagrams"></a>Co můžete dělat s diagramy tříd

- **Návrh**: úpravy kódu vašeho projektu úpravou diagramu tříd. Přidejte nové prvky a odstranit nežádoucí. Vaše změny se projeví v kódu.

- **Vizualizace**: pochopení vašeho projektu struktura zobrazením třídy ve vašem projektu v diagramu. Přizpůsobit diagramu tak, aby se mohli zaměřit na podrobností projektu, které vám nejvíc. Uložení diagramu pro pozdější použití pro demonstrační nebo v dokumentaci.

- **Refaktorovat**: přepište metody, přejmenování identifikátory, Refaktorovat parametry a implementovat rozhraní a abstraktní třídy.

## <a name="view-types-and-relationships"></a>Zobrazení typů a vztahů

Diagramy tříd zobrazit podrobnosti o různých typů, například jejich základní členové a vztahy mezi nimi. Vizualizaci tyto entity je dynamického zobrazení do kódu. To znamená, že můžete upravovat typy v návrháři a pak v tématu vaše úpravy projeví ve zdrojovém kódu entity. Podobně je udržováno diagramu tříd synchronizována s změny, které můžete provést soubory kódu.

> [!NOTE]
> Pokud projekt obsahuje diagramu tříd a projekt odkazuje na typ, který je umístěný v jiném projektu, diagramu tříd dokud sestavení projektu pro tento typ odkazovaného typu nezobrazuje. Podobně diagram nezobrazuje změny kódu externí entity, dokud je znovu sestavit projekt pro dané entity.

## <a name="class-diagram-workflow"></a>Pracovní postup diagram – třída

Diagramy tříd vám může pomoct pochopit struktura třídy projektů. Tyto projekty může být vytvořen pomocí jinými vývojáři nebo stačí aktualizačnímu programu na projektu, které jste sami vytvořili. Diagramy tříd můžete přizpůsobit, sdílet a prezentovat informace o projektu s ostatními.

Prvním krokem při nabízí informace o projektu je vytvoření diagramu tříd, který zobrazuje, co chcete zobrazit. Další informace najdete v tématu [přidat diagramu tříd](how-to-add-class-diagrams-to-projects.md). Můžete vytvořit více diagramů tříd pro projekt, který slouží k zobrazení různých zobrazení projektu, podmnožinu vybrané typy projektu nebo podmnožinu členů typů vybrané.

Kromě definovat, co každý třída diagram znázorňuje, můžete také změnit tak, aby informace jsou poskytovány; Další informace najdete v tématu [postupy: přizpůsobení diagramů tříd](how-to-customize-class-diagrams.md).

Po mít upřesnění diagramy jeden nebo více tříd, zkopírujte je do dokumentů Microsoft Office a jejich tisku nebo je exportovat jako soubory obrázků. Další informace najdete v tématu [postupy: kopírování elementů diagramu tříd do dokumentu sady Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [postupy: tisk diagramů tříd](how-to-print-class-diagrams.md) a [postupy: Export diagramů tříd jako obrázky](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Návrhář tříd nesleduje umístění zdrojových souborů, takže změna strukturu projektu nebo přesunutí zdrojové soubory v projektu může způsobit návrhář tříd ke ztrátě informací o typu, zejména typ zdroje typedef, základní třídy nebo typy přidružení. Může dojde k chybě, jako je **třída Návrhář nemůže zobrazit tento typ**. Pokud tak učiníte, přetáhněte upraveném nebo přemístěné zdrojový kód na diagramu tříd znovu a znovu ji zobrazit.

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../writing-code-in-the-code-and-text-editor.md)
- [Mapování závislostí napříč vaším řešením](../../modeling/map-dependencies-across-your-solutions.md)