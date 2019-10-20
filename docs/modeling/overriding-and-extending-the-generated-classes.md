---
title: Přepisování a rozšiřování vygenerovaných tříd
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c2386b7a7472f6b80457a5a803f6dfe886cc1d0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658338"
---
# <a name="override-and-extend-the-generated-classes"></a>Přepsat a zvětšit vygenerované třídy

Vaše definice DSL je platforma, na které můžete vytvořit výkonnou sadu nástrojů založenou na jazyce specifickém pro doménu. Mnoho rozšíření a přizpůsobení lze provést přepsáním a rozšířením tříd, které jsou generovány z definice DSL. Tyto třídy zahrnují nejen třídy domény, které jste explicitně definovali v diagramu definice DSL, ale také jiné třídy, které definují panel nástrojů, Průzkumníka, serializaci a tak dále.

## <a name="extensibility-mechanisms"></a>Mechanismy rozšiřitelnosti

K dispozici je několik mechanismů umožňujících rozšiřování vygenerovaného kódu.

### <a name="override-methods-in-a-partial-class"></a>Přepsání metod v částečné třídě

Definice částečné třídy umožňují definovat třídu na více než jednom místě. To umožňuje oddělit generovaný kód od kódu, který píšete sami. V ručně psaném kódu můžete přepsat třídy zděděné generovaným kódem.

Například pokud v definici DSL definujete doménovou třídu s názvem `Book`, můžete napsat vlastní kód, který přidá metody přepsání:

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> Chcete-li přepsat metody ve vygenerované třídě, vždy zapište kód v souboru, který je oddělen od generovaných souborů. Soubor je obvykle obsažen ve složce s názvem CustomCode. Pokud provedete změny generovaného kódu, ztratí se, když kód znovu vygenerujete z definice DSL.

Chcete-li zjistit, jaké metody lze přepsat, zadejte do třídy **přepsání** a za ní mezeru. Popisek technologie IntelliSense vám sdělí, jaké metody lze přepsat.

### <a name="double-derived-classes"></a>Dvojité odvozené třídy

Většina metod v generovaných třídách je děděna z pevné sady tříd v oborech názvů modelování. Nicméně některé metody jsou definovány ve vygenerovaném kódu. Obvykle to znamená, že je nemůžete přepsat. nelze přepsat jednu částečnou třídu metodami, které jsou definovány v jiné částečné definici stejné třídy.

Tyto metody však můžete přepsat nastavením příznaku pro **vygenerování dvojitého odvození** pro doménovou třídu. To způsobí, že budou vygenerovány dvě třídy, jedna je abstraktní základní třída druhé. Všechny definice metody a vlastností jsou v základní třídě a pouze konstruktor je v odvozené třídě.

Například v ukázkové knihovně. DSL má `CirculationBook` doménová třída `Generates``Double Derived` vlastnost nastavenou na `true`. Generovaný kód pro tuto doménovou třídu obsahuje dvě třídy:

- `CirculationBookBase`, což je abstraktní a který obsahuje všechny metody a vlastnosti.

- `CirculationBook`, která je odvozena z `CirculationBookBase`. Je prázdný, s výjimkou jeho konstruktorů.

Chcete-li přepsat libovolnou metodu, vytvoříte částečnou definici odvozené třídy, jako je například `CirculationBook`. Můžete přepsat jak vygenerované metody, tak metody zděděné z rozhraní modelování.

Tuto metodu lze použít u všech typů element, včetně prvků modelu, vztahů, tvarů, diagramů a konektorů. Můžete také přepsat metody jiných generovaných tříd. Některé generované třídy, jako je například ToolboxHelper, jsou vždy dvakrát odvozené.

### <a name="custom-constructors"></a>Vlastní konstruktory

Konstruktor nelze přepsat. I v případě dvojitě odvozených tříd musí být konstruktor v odvozené třídě.

Pokud chcete poskytnout vlastní konstruktor, můžete to provést nastavením `Has Custom Constructor` pro doménovou třídu v definici DSL. Když kliknete na možnost **transformovat všechny šablony**, vygenerovaný kód nebude obsahovat konstruktor pro tuto třídu. Bude obsahovat volání chybějícího konstruktoru. Způsobí to, že při sestavování řešení dojde k chybě. Dvojitým kliknutím na zprávu o chybách se zobrazí komentář ve vygenerovaném kódu, který vysvětluje, co byste měli poskytnout.

Zapište částečnou definici třídy v souboru, který je oddělený od generovaných souborů a poskytněte konstruktor.

### <a name="flagged-extension-points"></a>Rozšiřovací body s příznakem

Rozšiřovací bod označený příznakem je místo v definici DSL, kde můžete nastavit vlastnost nebo zaškrtávací políčko, abyste označili, že budete poskytovat vlastní metodu. Vlastní konstruktory jsou jeden příklad. Mezi další příklady patří nastavení `Kind` doménové vlastnosti na počítané nebo vlastní úložiště nebo nastavení příznaku **vlastní** v Tvůrci připojení.

V každém případě když nastavíte příznak a znovu vygenerujete kód, bude výsledkem chyba sestavení. Dvojitým kliknutím na chybu zobrazíte komentář s vysvětlením, co je třeba zadat.

### <a name="rules"></a>Pravidly

Správce transakcí umožňuje definovat pravidla, která se spouštějí před koncem transakce, ve které došlo k určené události, jako je například změna vlastnosti. Pravidla se obvykle používají k údržbě synchronism mezi různými prvky v úložišti. Například pravidla se používají k ujištění, že diagram zobrazuje aktuální stav modelu.

Pravidla jsou definována na základě jednotlivých tříd, takže nemusíte mít kód, který zaregistruje pravidlo pro každý objekt. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Ukládat události

Úložiště modelování poskytuje mechanismus událostí, který můžete použít k naslouchání konkrétním typům změn v úložišti, včetně přidávání a mazání prvků, změn hodnot vlastností a tak dále. Obslužné rutiny události jsou volány po zavření transakce, ve které byly provedeny změny. Tyto události se obvykle používají k aktualizaci prostředků mimo obchod.

### <a name="net-events"></a>Události .NET

Můžete se přihlásit k odběru některých událostí v obrazcích. Například můžete naslouchat kliknutí myší na obrazec. Musíte napsat kód, který se přihlásí k odběru události pro každý objekt. Tento kód lze zapsat v přepsání InitializeInstanceResources ().

Některé události jsou generovány v ShapeFields, které se používají k vykreslení dekoratéry na tvar. Příklad naleznete v tématu [How to: zachycení kliknutí na tvar nebo dekoratér](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

K těmto událostem obvykle nedochází v rámci transakce. Pokud chcete provádět změny v úložišti, měli byste vytvořit transakci.