---
title: Hierarchie volání | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 823c61e7625850c680b52cd4ad9386ef0838d340
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660937"
---
# <a name="call-hierarchy"></a>Hierarchie volání
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hierarchie volání umožňuje procházet kód zobrazením všech volání a z vybrané metody, vlastnosti nebo konstruktoru. To vám umožní lépe pochopit, jak tok kódu a vyhodnotit účinky změn kódu. Můžete prozkoumat několik úrovní kódu pro zobrazení složitých řetězců volání metod a dalších vstupních bodů do kódu, který umožňuje prozkoumat všechny možné cesty provádění.

 Hierarchie volání je k dispozici v době návrhu, na rozdíl od zásobníku volání, který je zobrazen pomocí ladicího programu.

## <a name="using-call-hierarchy"></a>Použití hierarchie volání
 Chcete-li zobrazit okno **hierarchie volání** , klikněte pravým tlačítkem myši na název metody, vlastnosti nebo volání konstruktoru a pak klikněte na možnost **Zobrazit hierarchii volání**.

 Název člena se zobrazí v podokně stromového zobrazení v okně **hierarchie volání** . Pokud rozbalíte členský uzel, zobrazí se **volání na**_název člena_ a **volání z**poduzlů_názvů členů_ . Následující ilustrace znázorňuje tyto uzly v okně **hierarchie volání** .

 ![Hierarchie volání s otevřeným jedním uzlem](../../ide/reference/media/onenode.png "OneNode") Okno hierarchie volání

- Pokud rozbalíte **volání do** uzlu, zobrazí se všichni členové, kteří volají vybraného člena.

- Pokud rozbalíte **volání z** uzlu, zobrazí se všichni členové, kteří jsou voláni vybraným členem.

  Potom můžete rozbalit každý z těchto členů dílčího uzlu do **volání** a **volání z** uzlů. To vám umožní přejít do zásobníku volajících, jak je znázorněno na následujícím obrázku.

  ![Otevřít hierarchii volání více uzlů](../../ide/media/multiplenodes.png "MultipleNodes") Okno hierarchie volání

  Pro členy, které jsou definovány buď jako virtuální, nebo jako abstraktní, se zobrazí uzel **název metody přepsání** . Pro členy rozhraní se zobrazí uzel **implementující název metody** . Tyto rozbalitelné uzly se zobrazí na stejné úrovni jako **volání** a **volání z** uzlů.

  Pole **Rozsah hledání** na panelu nástrojů obsahuje možnosti pro **moje řešení**, **aktuální projekt**a **aktuální dokument**.

  Když vyberete podřízeného člena v podokně zobrazení stromu **hierarchie volání** :

- V podokně Podrobnosti o **hierarchii volání** se zobrazí všechny řádky kódu, ve kterých je podřízený člen volán z nadřazeného člena.

- **Okno Definice kódu**, pokud je otevřeno, zobrazuje kód pro vybraného člena. Toto okno je k dispozici v jazyce C# a C++. Další informace o tomto okně naleznete v tématu [zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> Hierarchie volání nenalezne odkazy na skupiny metod, které obsahují místo, kde je metoda přidána jako obslužná rutina události nebo je přiřazena delegátovi. Chcete-li najít všechny odkazy na metodu, můžete použít příkaz **Najít všechny odkazy** .

## <a name="shortcut-menu-items"></a>Položky místní nabídky
 Následující tabulka popisuje několik možností místní nabídky, které jsou k dispozici po kliknutí pravým tlačítkem myši na uzel v podokně stromového zobrazení.

|Položka kontextové nabídky|Popis|
|-----------------------|-----------------|
|**Přidat jako nový kořen**|Přidá vybraný uzel do podokna zobrazení stromu jako nový kořenový uzel. To vám umožní zaměřit se na pozornost konkrétního podstromu.|
|**Odebrat kořen**|Odebere vybraný kořenový uzel z podokna zobrazení stromu. Tato možnost je k dispozici pouze z kořenového uzlu.<br /><br /> K odebrání vybraného kořenového uzlu můžete použít také tlačítko **Odebrat kořenový** panel nástrojů.|
|**Přejít k definici**|Spustí příkaz Přejít k definici na vybraném uzlu. Tím přejdete k původní definici pro členské volání nebo definici proměnné.<br /><br /> Chcete-li spustit příkaz Přejít na definici, můžete také dvakrát kliknout na vybraný uzel nebo stisknout F12 na vybraném uzlu.|
|**Najít všechny odkazy**|Spustí příkaz Najít všechny odkazy na vybraném uzlu. Tím vyhledáte všechny řádky kódu v projektu, které odkazují na třídu nebo člen.<br /><br /> K spuštění příkazu Najít všechny odkazy na vybraném uzlu můžete také použít SHIFT + F12.|
|**Kopírovat**|Zkopíruje obsah vybraného uzlu (ale ne jeho poduzly).|
|**Aktualizovat**|Sbalí vybraný uzel, aby se znovu rozbalí aktuální informace.|
