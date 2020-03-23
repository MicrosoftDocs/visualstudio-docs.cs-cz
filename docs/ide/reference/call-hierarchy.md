---
title: Hledání volání metody
ms.date: 05/18/2018
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcedc6a49c0df84b4482f8030524d59d4336bcc8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595797"
---
# <a name="view-call-hierarchy"></a>Zobrazit hierarchii volání

Zobrazením hierarchie volání pro váš kód můžete procházet všechna volání a někdy i z vybrané metody, vlastnosti nebo konstruktoru. To umožňuje lépe pochopit, jak toky kódu a vyhodnotit účinky změn kódu. Můžete prozkoumat několik úrovní kódu pro zobrazení složitých řetězců volání metod a dalšívstupní body kódu. To umožňuje prozkoumat všechny možné cesty spuštění.

V sadě Visual Studio můžete zobrazit hierarchii volání v době návrhu. To znamená, že není třeba nastavit zarážku a spustit ladicí program pro zobrazení zásobníku volání za běhu.

## <a name="use-the-call-hierarchy-window"></a>Použití okna Hierarchie volání

Chcete-li zobrazit okno **Hierarchie volání,** klepněte pravým tlačítkem myši do editoru kódu na název metody, vlastnosti nebo volání konstruktoru a pak vyberte **zobrazit hierarchii volání**.

Název člena se zobrazí v podokně stromového zobrazení v okně **Hierarchie volání.** Pokud rozbalíte uzel **člena, volání na** *název člena*a pro C++, zobrazí se volání **z** názvu *člena*, zobrazí se poduzly.

Pro kód Jazyka C++ můžete zobrazit volání do a z člena:

![Hierarchie volání pro kód Jazyka C++ v sadě Visual Studio](media/call-hierarchy-cpp.png)

Pro kód jazyka C# a jazyka Visual Basic můžete zobrazit volání člena, ale ne volání z:

![Hierarchie volání pro kód Jazyka C# v sadě Visual Studio](media/call-hierarchy-csharp.png)

- Pokud rozbalíte **uzel Volání** do uzlu, zobrazí se všichni členové, kteří volají vybraného člena.

- Pro C++ f rozbalíte **volání z** uzlu, zobrazí se všechny členy, které jsou volány vybraným členem.

Potom můžete rozbalit každý volající člen zobrazíte jeho **volání na**, a pro C++, **Volání z** uzlů. To umožňuje přejít do zásobníku volajících, jak je znázorněno na následujícím obrázku:

![Okno Hierarchie volání s více rozšířenými úrovněmi](media/call-hierarchy-csharp-expanded.png)

Pro členy, které jsou definovány jako virtuální nebo abstraktní, se zobrazí uzel **názvu metody Overrides.** Pro členy rozhraní se zobrazí uzel **názvu metody Implements.** Tyto rozbalitelné uzly se zobrazí na stejné úrovni jako **volání do** a **volání z** uzlů.

Pole **Obor hledání** na panelu nástrojů obsahuje volby pro Moje **řešení**, Aktuální **projekt**a Aktuální **dokument**.

Když vyberete podřízeného člena v podokně stromového zobrazení **Hierarchie volání:**

- Podokno podrobností **hierarchie volání** zobrazuje všechny řádky kódu, ve kterých je tento podřízený člen volán z nadřazeného člena.

- Okno **Definice kódu,** pokud je otevřeno, zobrazí kód vybraného člena (pouze C++). Další informace o tomto okně naleznete [v tématu Zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> Funkce **Hierarchie volání** nenalezne odkazy na skupiny metod, které zahrnují místa, kde je metoda přidána jako obslužná rutina události nebo je přiřazena delegátovi. Chcete-li najít všechny odkazy na metodu, můžete použít příkaz **Najít všechny odkazy.**

## <a name="shortcut-menu-items"></a>Položky místní nabídky

Následující tabulka popisuje několik možností místní nabídky, které jsou k dispozici po klepnutí pravým tlačítkem myši na uzel v podokně zobrazení stromu.

|Položka kontextové nabídky|Popis|
| - |-----------------|
|**Přidat jako nový kořen**|Přidá vybraný uzel do podokna stromového zobrazení jako nový kořenový uzel. To vám umožní zaměřit svou pozornost na konkrétní podstrom.|
|**Odebrat kořenový adresář**|Odebere vybraný kořenový uzel z podokna zobrazení stromu. Tato možnost je k dispozici pouze z kořenového uzlu.<br /><br /> K odebrání vybraného kořenového uzlu můžete také použít tlačítko **Odebrat kořenový** panel nástrojů.|
|**Přejít na definici**|Spustí příkaz Přejít na definici na vybraném uzlu. Tím přejdete na původní definici členského volání nebo definice proměnné.<br /><br /> Chcete-li spustit příkaz Přejít na definici, můžete také poklepat na vybraný uzel nebo stisknout klávesu F12 na vybraném uzlu.|
|**Najít všechny odkazy**|Spustí příkaz Najít všechny odkazy na vybraném uzlu. To vyhledá všechny řádky kódu v projektu, které odkazují na třídu nebo člena.<br /><br /> Můžete také použít SHIFT+F12 ke spuštění příkazu Najít všechny odkazy na vybraném uzlu.|
|**Kopírovat**|Zkopíruje obsah vybraného uzlu (ale ne jeho poduzly).|
|**Obnovení**|Sbalí vybraný uzel tak, aby se při jeho opětovném rozbalení zosykala aktuální informace.|
