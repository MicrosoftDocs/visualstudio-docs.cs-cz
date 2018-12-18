---
title: Přepisování a rozšiřování vygenerovaných tříd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a5aef90403babfd7a30812cac59b8c0c5acff79f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933427"
---
# <a name="overriding-and-extending-the-generated-classes"></a>Přepisování a rozšiřování vygenerovaných tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vaše definice DSL je platforma, na kterém můžete vytvářet výkonná sada nástrojů, které jsou založeny na jazyka specifického pro doménu. Mnoho rozšíření a přizpůsobení je možné provádět pomocí přepisování a rozšiřování třídy, které jsou generovány z definice DSL. Tyto třídy zahrnují nejen doménové třídy, které jste definovali explicitní v diagramem definice DSL, ale také další třídy, které definují sady nástrojů, Průzkumníka, serializace a tak dále.  
  
## <a name="extensibility-mechanisms"></a>Mechanismus rozšíření  
 Aby bylo možné rozšířit generovaného kódu jsou k dispozici několik mechanismů.  
  
### <a name="overriding-methods-in-a-partial-class"></a>Přepsání metody v dílčí třídě  
 Definicí částečné třídy umožnit třídě definovat více než jednom místě. To umožňuje kód, který si sami napíšete nezávislá na infrastruktuře generovaného kódu. Ve vašem kódu ručně psanou můžete přepsat třídy dědí generovaného kódu.  
  
 Například, pokud v definici DSL definujete doménovou třídu s názvem `Book`, můžete napsat vlastní kód, který přidá přepsání metody:  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  Přepsání metody ve vygenerované třídě, vždy napište svůj kód v souboru, který je oddělen od generované soubory. Soubor je obvykle obsažen ve složce s názvem CustomCode. Pokud provedete změny generovaný kód, budou ztraceny při opětovném vygenerování kódu v definici DSL.  
  
 Chcete-li zjistit, jaké metody můžete přepsat, zadejte **přepsat** ve třídě, za nímž následuje mezera. Popisu tlačítka technologie IntelliSense vám sdělí, jaké metody se dá přepsat.  
  
### <a name="double-derived-classes"></a>Double odvozené třídy  
 Většina metod v generované třídy dědí z dlouhodobého sadu tříd v oborech názvů modelování. Nicméně některé metody jsou definovány v generovaném kódu. Obvykle to znamená, že je nelze přepsat nelze přepsat jedné třídy na částečné metody, které jsou definovány v jiné částečné deklaraci stejné třídy.  
  
 Tyto metody však můžete přepsat tak, že nastavíte **Generates Double Derived** příznak pro doménovou třídu. Tato dvě třídy způsobí, že chcete vygenerovat, jeden je abstraktní základní třída druhé. Všechny definice metody a vlastnosti jsou v základní třídě a pouze konstruktor je v odvozené třídě.  
  
 Například v ukázce Library.dsl `CirculationBook` má doménová třída `Generates``Double Derived` nastavenou na `true`. Generovaný kód pro danou třídu domény obsahuje dvě třídy:  
  
- `CirculationBookBase`, což je abstraktní a který obsahuje všechny metody a vlastnosti.  
  
- `CirculationBook`, který je odvozen z `CirculationBookBase`. Je prázdný, s výjimkou jejích konstruktorů.  
  
  Pokud chcete přepsat libovolné metody, vytvoříte částečnou definici odvozené třídy jako `CirculationBook`. Můžete přepsat generované metody a metody, které dědí z rozhraní pro modelování.  
  
  Tuto metodu můžete použít se všemi typy elementu, včetně prvků modelu, relace, tvary, diagramy a konektory. Můžete také přepsat metody jiné generované třídy. Některé vygenerované třídy, jako ToolboxHelper jsou vždy odvozené double.  
  
### <a name="custom-constructors"></a>Vlastní konstruktory  
 Konstruktor nemůže přepsat. I v double odvozené třídy musí být konstruktor v odvozené třídě.  
  
 Pokud chcete poskytnout vlastní konstruktor, můžete to provést tak, že nastavíte `Has Custom Constructor` pro doménovou třídu v definici DSL. Po kliknutí na **Transformovat všechny šablony**, vygenerovaný kód nebude obsahovat konstruktor pro danou třídu. Bude zahrnovat volání konstruktoru chybí. To způsobí, že zpráva o chybě při sestavování řešení. Dvakrát klikněte na Zobrazit komentář ve vygenerovaném kódu, který vysvětluje, co byste měli poskytnout zprávy o chybách.  
  
 Zapsat definice částečné třídy v souboru, který je oddělený od generované soubory a Poskytněte konstruktor.  
  
### <a name="flagged-extension-points"></a>Označené příznakem Rozšiřovací body  
 Označené příznakem rozšiřovací bod je místo, kde v definici DSL, kde můžete nastavit políčko označující, že poskytnete vlastní metodu nebo vlastnost. Vlastní konstruktory jsou jedním z příkladů. Další příklady nastavení `Kind` počítané nebo vlastní úložiště nebo nastavení vlastnosti domény **je vlastní** příznak v Tvůrce připojení.  
  
 V každém případě pokud nastavte příznak a znovu vygenerovat kód, sestavení způsobí chybu. Klikněte dvakrát na chybu, která vysvětluje, co je nutné zadat poznámku.  
  
### <a name="rules"></a>pravidla  
 Správce transakcí umožňuje definovat pravidla, která spustí před ukončením transakce, ve kterém má určené události došlo, jako je například změna vlastnosti. Pravidla se obvykle používají k údržbě synchronism mezi různé prvky v úložišti. Například se používají pravidla, abyste měli jistotu, že diagram zobrazuje aktuální stav modelu.  
  
 Pravidla jsou definovaná na základě každé třídy, takže není nutné mít kód, který registruje pravidlo pro každý objekt. Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
### <a name="store-events"></a>Store události  
 Modelování úložiště poskytuje mechanismus události, kterou můžete použít k naslouchání pro konkrétní typy změn v úložišti, včetně přidání a odstranění prvků, změny hodnot vlastností a tak dále. Po uzavření transakce, ve kterém byly provedeny změny jsou volány obslužné rutiny události. Tyto události se obvykle používají k aktualizaci prostředky mimo úložiště.  
  
### <a name="net-events"></a>Události .NET  
 Můžete odebírat některé události ve tvarech. Například může naslouchat kliknutí myší na obrazec. Je nutné napsat kód, který se přihlásí k této události pro každý objekt. Tento kód je možné psát v přepsání InitializeInstanceResources().  
  
 Některé události se generují u ShapeFields, které se používají na obrazec nakreslit dekorátory. Příklad najdete v tématu [postupy: zachycení kliknutí na obrazec či Dekorátor](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 Tyto události obvykle nedojde v transakci. Pokud chcete provést změny v úložišti, měli byste vytvořit transakci.



