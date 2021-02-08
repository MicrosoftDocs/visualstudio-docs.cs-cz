---
title: Hledání volání metody
description: Naučte se používat okno hierarchie volání k procházení všech volání, a to v rámci vybrané metody, vlastnosti nebo konstruktoru.
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7384376b604f2097d68bf8bac06b2af0158e09b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836472"
---
# <a name="view-call-hierarchy"></a>Zobrazit hierarchii volání

Zobrazením hierarchie volání pro váš kód můžete procházet všechna volání do a někdy z, vybrané metody, vlastnosti nebo konstruktoru. To vám umožní lépe pochopit, jak toky kódu a vyhodnotit účinky změn kódu. Pro zobrazení složitých řetězců volání metod a dalších vstupních bodů do kódu lze prošetřit několik úrovní kódu. To vám umožní prozkoumat všechny možné cesty spuštění.

V aplikaci Visual Studio můžete zobrazit hierarchii volání v době návrhu. To znamená, že nemusíte nastavovat zarážku a spustit ladicí program pro zobrazení zásobníku volání runtime.

## <a name="use-the-call-hierarchy-window"></a>Použití okna hierarchie volání

Chcete-li zobrazit okno **hierarchie volání** , klikněte pravým tlačítkem myši v editoru kódu na název metody, vlastnosti nebo volání konstruktoru a pak vyberte **Zobrazit hierarchii volání**.

Název člena se zobrazí v podokně stromového zobrazení v okně **hierarchie volání** . Rozbalíte-li členský uzel, **volání na** *název člena* a pro jazyk C++, budou **volána volání z** *názvu člena*, poduzly.

Pro kód jazyka C++ vidíte volání do a od člena:

![Hierarchie volání pro kód jazyka C++ v aplikaci Visual Studio](media/call-hierarchy-cpp.png)

Pro kód C# a Visual Basic můžete zobrazit volání členu, ale ne volání z:

![Hierarchie volání pro kód jazyka C# v aplikaci Visual Studio](media/call-hierarchy-csharp.png)

- Pokud rozbalíte **volání do** uzlu, zobrazí se všichni členové, kteří volají vybraného člena.

- V jazyce C++, f rozšíříte **volání z** uzlu, jsou zobrazeny všichni členové, kteří jsou voláni vybraným členem.

Pak můžete rozbalit každého volajícího člena a zobrazit jeho **volání do** a pro jazyk C++ **volání z** uzlů. To vám umožní přejít do zásobníku volajících, jak je znázorněno na následujícím obrázku:

![Rozbalení okna hierarchie volání s více úrovněmi](media/call-hierarchy-csharp-expanded.png)

Pro členy, které jsou definovány buď jako virtuální, nebo jako abstraktní, se zobrazí uzel **název metody přepsání** . Pro členy rozhraní se zobrazí uzel **implementující název metody** . Tyto rozbalitelné uzly se zobrazí na stejné úrovni jako **volání** a **volání z** uzlů.

Pole **Rozsah hledání** na panelu nástrojů obsahuje možnosti pro **moje řešení**, **aktuální projekt** a **aktuální dokument**.

Když vyberete podřízeného člena v podokně zobrazení stromu **hierarchie volání** :

- V podokně Podrobnosti o **hierarchii volání** se zobrazí všechny řádky kódu, ve kterých je podřízený člen volán z nadřazeného člena.

- Okno **definice kódu** , pokud je otevřeno, zobrazuje kód pro vybraného člena (pouze C++). Další informace o tomto okně naleznete v tématu [zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> Funkce **hierarchie volání** nenalezne odkazy na skupiny metod, které obsahují místo, kde je metoda přidána jako obslužná rutina události nebo je přiřazena delegátovi. Chcete-li najít všechny odkazy na metodu, můžete použít příkaz **Najít všechny odkazy** .

## <a name="shortcut-menu-items"></a>Položky místní nabídky

Následující tabulka popisuje několik možností místní nabídky, které jsou k dispozici po kliknutí pravým tlačítkem myši na uzel v podokně stromového zobrazení.

|Položka kontextové nabídky|Description|
| - |-----------------|
|**Přidat jako nový kořen**|Přidá vybraný uzel do podokna zobrazení stromu jako nový kořenový uzel. To vám umožní zaměřit se na pozornost konkrétního podstromu.|
|**Odebrat kořen**|Odebere vybraný kořenový uzel z podokna zobrazení stromu. Tato možnost je k dispozici pouze z kořenového uzlu.<br /><br /> K odebrání vybraného kořenového uzlu můžete použít také tlačítko **Odebrat kořenový** panel nástrojů.|
|**Přejít k definici**|Spustí příkaz Přejít k definici na vybraném uzlu. Tím přejdete k původní definici pro členské volání nebo definici proměnné.<br /><br /> Chcete-li spustit příkaz Přejít na definici, můžete také dvakrát kliknout na vybraný uzel nebo stisknout F12 na vybraném uzlu.|
|**Najít všechny odkazy**|Spustí příkaz Najít všechny odkazy na vybraném uzlu. Tím vyhledáte všechny řádky kódu v projektu, které odkazují na třídu nebo člen.<br /><br /> K spuštění příkazu Najít všechny odkazy na vybraném uzlu můžete také použít SHIFT + F12.|
|**Kopírovat**|Zkopíruje obsah vybraného uzlu (ale ne jeho poduzly).|
|**Aktualizovat**|Sbalí vybraný uzel, aby se znovu rozbalí aktuální informace.|
