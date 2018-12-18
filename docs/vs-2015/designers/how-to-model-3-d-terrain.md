---
title: 'Postupy: modelování 3D terénu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fae94fe5e7474580f8867f531fc41d0ce6781cf8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940512"
---
# <a name="how-to-model-3-d-terrain"></a>Postupy: Modelování 3D terénu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje způsob použití Editoru modelů a vytvořte model 3D terénu.  
  
 Tento dokument vysvětluje tyto činnosti:  
  
-   Přidání objektů do scény  
  
-   Výběrem tváří a body  
  
-   Možnosti překladu  
  
-   Použití **rozdělit plochu** nástroj  
  
-   Rámců objekt návrhové ploše  
  
## <a name="creating-a-3-d-terrain-model"></a>Vytvoření modelu 3D terénu  
 Můžete vytvořit 3D terénu rozdělení roviny provést další tváře a potom manipulace s jejich vrcholy pro vytvoření zajímavých funkcí terénu.  
  
 Jakmile budete hotovi, model by měl vypadat nějak takto:  
  
 ![3&#45;D scény, který znázorňuje model terénu](../designers/media/digit-terrain-model.png "číslice terénu modelu")  
  
 Než začnete, ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.  
  
#### <a name="to-create-a-3-d-terrain-model"></a>Chcete-li vytvořit model 3D terénu  
  
1. Vytvoření 3D modelu chcete pracovat. Informace o tom, jak přidat modelu do projektu naleznete v části Začínáme v [editoru modelů](../designers/model-editor.md).  
  
2. Přidáte do roviny do scény. V **nástrojů**v části **tvary**vyberte **roviny** a přesuňte jej na návrhovou plochu.  
  
   > [!TIP]
   >  Pro usnadnění práce s objekt roviny, můžete ho rámce v návrhové ploše. V **vyberte** režimu, vyberte objekt roviny a pak na panelu nástrojů editoru modelů, zvolte **orámovat objekt** tlačítko.  
  
3. Zadejte režimu výběru ploch. Na panelu nástrojů editoru modelů **tváří vybrat**.  
  
4. Rozdělit plochy. V režimu výběru ploch zvolte jednou rovinou aktivace pro výběr a klikněte na tlačítko ho znovu a vyberte jeho pouze pro rozpoznávání tváře. Na panelu nástrojů editoru modelů **rozdělit plochu**. Tento postup přidá nové vrcholy k rovině ho rozdělit do čtyř oddílů stejně velké.  
  
5. Vytvořte další dělení. Pomocí nových ploch stále vybranou, zvolte **rozdělit plochu** ještě dvakrát. Tím se vytvoří celkem 64 tváří. Vytvořením další dělení můžete udělit terénu více podrobností.  
  
6. Zadejte režim výběru bodu. Na panelu nástrojů editoru modelů **vybrat bod**.  
  
7. Změna bodu, aby vytvořil terénu funkci. V režimu výběru bodu, vyberte jednu z bodů a pak na panelu nástrojů editoru modelů, zvolte **přeložit** nástroj. Pole, který představuje bod se zobrazí na návrhové ploše. Použijte na zelenou šipku a přesunout do pole a změna výšky bodu. Opakujte tento krok pro různých fázích pro vytvoření zajímavých funkcí terénu.  
  
   > [!TIP]
   >  Můžete vybrat několik bodů najednou k jejich úpravě jednotným způsobem.  
  
   Model terénu je dokončena. Tady je znovu finálního modelu s Phongova stínování použít:  
  
   ![3&#45;D scény, který znázorňuje model terénu](../designers/media/digit-terrain-model.png "číslice terénu modelu")  
  
   Tento model terénu slouží k předvedení efekt přechodu shaderu, který je popsaný v [postupy: vytvoření shaderu přechodu na základě geometrie](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## <a name="see-also"></a>Viz také  
 [Editor modelů](../designers/model-editor.md)



