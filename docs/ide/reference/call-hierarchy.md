---
title: Vyhledejte volání metody
ms.date: 05/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f386d3d73de45c539752207fb55200e8e8ee715
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905951"
---
# <a name="view-call-hierarchy"></a>Zobrazit hierarchii volání

Zobrazením hierarchie volání pro svůj kód můžete procházet všechna volání do a někdy z vybrané metody, vlastnosti nebo konstruktoru. To umožňuje lépe porozumět toku kódu a vyhodnotit vliv změn kódu. Můžete zkontrolovat několik úrovní kódu zobrazíte komplexní řetězů, volání metod a další vstupní body do kódu. To umožňuje prozkoumat všemi možnými cestami spuštění.

V sadě Visual Studio můžete zobrazit hierarchii volání v době návrhu. To znamená, že není nutné nastavit zarážky a spuštění ladicího programu, chcete-li zobrazit zásobník volání za běhu.

## <a name="use-the-call-hierarchy-window"></a>Použití okna hierarchie volání

Chcete-li zobrazit **hierarchie volání** okna, klikněte pravým tlačítkem na název metody, vlastnosti nebo volání konstruktoru editoru kódu a pak vyberte **zobrazit hierarchii volání**.

Název člena se zobrazí v podokně se stromovým zobrazením v **hierarchie volání** okna. Pokud rozbalíte uzel člen **volání do** *název člena*a pro C++, **volání z** *název člena*, zobrazí podřízených uzlů.

Pro kód C++ můžete zobrazit volání do a z člena:

![Hierarchie volání pro kód C++ v sadě Visual Studio](media/call-hierarchy-cpp.png)

Pro C# a kód jazyka Visual Basic, můžete zobrazit volání na člen, ale ne volání od:

![Hierarchie pro volání C# kódu v sadě Visual Studio](media/call-hierarchy-csharp.png)

- Pokud rozbalíte **volání do** uzlu, všechny členy, že se zobrazují volání vybraného členu.

- Pro jazyk C++, f rozšíření **volání z** se zobrazí uzel, všechny členy, které jsou volány vybraného člena.

Můžete rozbalit každého volání člena zobrazíte jeho **volání do**a pro C++, **volání z** uzly. To vám umožní přejít do zásobníku volání, jak je znázorněno na následujícím obrázku:

![Hierarchie volání – okno s více úrovněmi rozšířit](media/call-hierarchy-csharp-expanded.png)

Pro členy, které jsou definovány jako virtuální nebo abstraktní **název metody přepsání** uzel se objeví. Pro členy rozhraní **název metody implementuje** uzel se objeví. Tyto uzly rozšíření se zobrazí na stejné úrovni jako **volání do** a **volání z** uzly.

**Obor vyhledávání** na panelu nástrojů obsahuje možnosti pro **Moje řešení**, **aktuální projekt**, a **aktuální dokument**.

Když vyberete podřízeného člena v **hierarchie volání** podokně se stromovým zobrazením:

- **Hierarchie volání** podokně podrobností se zobrazí všechny řádky kódu, ve kterém tento podřízený člen je volána z nadřazeného člena.

- **Definice kódu** , pokud otevřete, zobrazí se okno kód pro vybraného člena (pouze C++). Další informace o tomto okně najdete v tématu [zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> **Hierarchie volání** funkce nenajde metoda odkazy na skupinu, což zahrnuje místa, kde se přidá jako obslužná rutina události metodu, nebo je přiřazená delegáta. Pokud chcete najít všechny odkazy na metodu, můžete použít **najít všechny odkazy** příkazu.

## <a name="shortcut-menu-items"></a>Položky místní nabídky

Následující tabulka popisuje několik možnosti místní nabídky, které jsou k dispozici, když kliknete pravým tlačítkem myši na uzel v podokně se stromovým zobrazením.

|Položka kontextové nabídky|Popis|
| - |-----------------|
|**Přidat jako nový kořen**|Přidá zvolený uzel podokně se stromovým zobrazením jako nový kořenový uzel. To umožňuje zaměřit se na konkrétní podstrom vaši pozornost.|
|**Odebrat kořen**|Odebere vybrané kořenový uzel v podokně se stromovým zobrazením. Tato možnost je dostupná pouze z kořenového uzlu.<br /><br /> Můžete také použít **odebrat kořenové** tlačítka panelu nástrojů, které chcete odebrat vybrané kořenového uzlu.|
|**Přejít k definici**|Spustí příkaz Přejít k definici ve zvoleném uzlu. Toto odkazuje na původní definice pro člen volání nebo definicí proměnné.<br /><br /> Ke spuštění příkazu Přejít k definici, můžete také dvakrát klikněte na vybraný uzel nebo stisknutím klávesy F12 ve zvoleném uzlu.|
|**Najít všechny odkazy**|Spustí příkaz Najít všechny odkazy na vybraný uzel. To tuto referenční třídu nebo člen vyhledá všechny řádky kódu ve vašem projektu.<br /><br /> SHIFT + F12 můžete také použít ke spuštění příkazu Najít všechny odkazy na vybraný uzel.|
|**kopírování**|Zkopíruje obsah vybraného uzlu (ale ne jeho podřízené uzly).|
|**Aktualizace**|Sbalí vybraný uzel tak, aby znovu ho rozbalíte, zobrazí aktuální informace.|