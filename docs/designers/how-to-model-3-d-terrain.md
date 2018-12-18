---
title: 'Postupy: modelování 3D terénu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24fdf5f6c80dbb9d338b4c655b7cea05592a91ac
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2018
ms.locfileid: "38977743"
---
# <a name="how-to-model-3d-terrain"></a>Postupy: modelování 3D terénu

Tento článek ukazuje, jak vytvořit model 3D terénu pomocí Editoru modelů.

## <a name="create-a-3d-terrain-model"></a>Vytvoření modelu 3D terénu

Můžete vytvořit 3D terénu rozdělení roviny provést další tváře a potom manipulace s jejich vrcholy pro vytvoření zajímavých funkcí terénu.

Jakmile budete hotovi, model by měl vypadat nějak takto:

![3&#45;D scény, který znázorňuje model terénu](../designers/media/digit-terrain-model.png)

Než začnete, ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.

1.  Vytvoření 3D modelu, se kterým chcete pracovat. Informace o tom, jak přidat modelu do projektu naleznete v části Začínáme v [editoru modelů](../designers/model-editor.md).

2.  Přidáte do roviny do scény. V **nástrojů**v části **tvary**vyberte **roviny** a přesuňte jej na návrhovou plochu.

    > [!TIP]
    > Pro usnadnění práce s objekt roviny, můžete ho rámce v návrhové ploše. V **vyberte** režimu, vyberte objekt roviny a pak na panelu nástrojů editoru modelů, zvolte **orámovat objekt** tlačítko.

3.  Zadejte režimu výběru ploch. Na panelu nástrojů editoru modelů **tváří vybrat**.

4.  Rozdělit plochy. V režimu výběru ploch zvolte jednou rovinou aktivace pro výběr a klikněte na tlačítko ho znovu a vyberte jeho pouze pro rozpoznávání tváře. Na panelu nástrojů editoru modelů **rozdělit plochu**. Tento postup přidá nové vrcholy k rovině ho rozdělit do čtyř oddílů stejně velké.

5.  Vytvořte další dělení. Pomocí nových ploch stále vybranou, zvolte **rozdělit plochu** ještě dvakrát. Tím se vytvoří celkem 64 tváří. Vytvořením další dělení můžete udělit terénu více podrobností.

6.  Zadejte režim výběru bodu. Na panelu nástrojů editoru modelů **vybrat bod**.

7.  Změna bodu, aby vytvořil terénu funkci. V režimu výběru bodu, vyberte jednu z bodů a pak na panelu nástrojů editoru modelů, zvolte **přeložit** nástroj. Pole, který představuje bod se zobrazí na návrhové ploše. Použijte na zelenou šipku a přesunout do pole a změna výšky bodu. Opakujte tento krok pro různých fázích pro vytvoření zajímavých funkcí terénu.

    > [!TIP]
    > Můžete vybrat několik bodů najednou k jejich úpravě jednotným způsobem.

Model terénu je dokončena. Tady je znovu finálního modelu s Phongova stínování použít:

![3&#45;D scény, který znázorňuje model terénu](../designers/media/digit-terrain-model.png)

Tento model terénu slouží k předvedení efekt přechodu shaderu, který je popsaný v [postupy: vytvoření shaderu přechodu na základě geometrie](../designers/how-to-create-a-geometry-based-gradient-shader.md).

## <a name="see-also"></a>Viz také:

- [Editor modelů](../designers/model-editor.md)