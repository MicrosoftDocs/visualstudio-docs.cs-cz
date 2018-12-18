---
title: 'Postupy: Změna mezi zápisem člena a zápisem asociace (návrhář tříd)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdb4f28fc367b309a015a3faa8f749e2512db879
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957798"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Postupy: změna mezi zápisem člena a zápisem asociace v Návrháři tříd

V **návrhář tříd**, můžete změnit způsob diagramu tříd představuje relaci přidružení mezi dvěma typy z notace členů notace přidružení a naopak. Členy zobrazené jako Asociační čáry často poskytují užitečné vizualizaci jak typy souvisejí.

> [!NOTE]
> Přidružení relace může být reprezentován jako člen vlastnost nebo pole. Chcete-li změnit notace členů notace přidružení, musí mít jeden typ členem jiného typu. Notace přidružení změnit na notace členů, existují dva typy musí být připojen přidružení čára. Další informace najdete v tématu [postupy: vytvoření přidružení typů bBetween](how-to-create-associations-between-types.md). Pokud projekt obsahuje více diagramů tříd, změny, které provedete způsob diagram zobrazuje přidružení vztahy ovlivňují jenom tento diagram. Změnit způsob jiný diagram zobrazuje přidružení vztahů, otevřete nebo zobrazit tento diagram a proveďte tyto kroky.

## <a name="to-change-member-notation-to-association-notation"></a>Chcete-li změnit notace členů do notace přidružení

1.  Z uzlu projektu v Průzkumníku řešení otevřete soubor třídy diagram (.cd).

2.  V obrazce typu v diagramu tříd, klikněte pravým tlačítkem člen vlastnost nebo pole představující přidružení a zvolte **zobrazit jako přidružení**.

    > [!TIP]
    > Pokud žádné vlastnosti nebo pole jsou viditelné v obrazce typu, mohou být sbaleny přihrádky ve tvaru. Rozšířit obrazce typu, klikněte dvakrát na název prostředí nebo klikněte pravým tlačítkem na obrazce typu a vyberte **rozbalte**.

    Člen dané zařízení zmizí z prostředí v obrazce typu a řádku s přidružení se zobrazí oba typy připojení. Přidružení řádek označený verzí název vlastnost nebo pole.

## <a name="to-change-association-notation-to-member-notation"></a>Chcete-li změnit notace přidružení k notace členů

Na diagramu tříd, klikněte pravým tlačítkem na ose přidružení a zvolte **zobrazit jako vlastnost** nebo **zobrazit jako pole** podle potřeby. Přidružení řádku zmizí, a vlastnost zobrazí v příslušné prostředí v rámci jeho obrazce typu v diagramu.

## <a name="see-also"></a>Viz také

- [Postupy: vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md)
- [Postupy: zobrazení dědičnosti mezi typy](how-to-view-inheritance-between-types.md)
- [Zobrazování typů a vztahů](viewing-types-and-relationships.md)
- [Postupy: vizualizace asociace kolekce](how-to-visualize-a-collection-association.md)