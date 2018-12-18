---
title: Práce s kódem jazyka Visual C++ (návrhář tříd)
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 109c2408e16c5ca4943855889191733234778761
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958448"
---
# <a name="work-with-visual-c-code-in-class-designer"></a>Práce s kódem jazyka Visual C++ v Návrháři tříd

**Třídy návrháře** zobrazí návrhové ploše názvem *diagramu tříd* , který poskytuje vizuální reprezentace elementy kódu v projektu. Diagramy tříd můžete použít k návrhu a vizualizovat třídami a ostatními typy v projektu.

**Třídy návrháře** podporuje následující elementy kódu C++:

- Třídy (podobá obrazce spravované třídy, s tím rozdílem, že může mít více vztahů dědičnost)

- Anonymní – třída (zobrazí se zobrazení tříd vygenerovaný název anonymního typu)

- Šablony třídy

- Struktura

- Výčet

- Makro (zobrazí se po zpracování zobrazení makra)

- Definice TypeDef

> [!NOTE]
> To však není stejný jako diagramu tříd UML, který můžete vytvořit v projektu modelování. Další informace najdete v tématu [diagramů tříd UML: referenční dokumentace](../../modeling/uml-class-diagrams-reference.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Řešení potíží s typu řešení a zobrazit problémy

### <a name="location-of-source-files"></a>Umístění zdrojových souborů

**Třídy návrháře** není udržování přehledu o umístění zdrojových souborů. Proto, pokud změníte strukturu projektu nebo přesunout zdrojové soubory v projektu, **návrhář tříd** může dojít ke ztrátě sledovat typu (zejména typ zdroje typedef, základní třídy nebo přidružení typů). Může dojít chybě, jako **třída Návrhář nemůže zobrazit tento typ**. Pokud tak učiníte, přetáhněte upraveném nebo přemístěné zdrojový kód na diagramu tříd znovu a znovu ji zobrazit.

### <a name="update-and-performance-issues"></a>Problémy se aktualizace a výkonu

Pro projekty Visual C++ může trvat 30 – 60 sekund pro změnu v zdrojový soubor, který se zobrazí v diagramu tříd. Toto zpoždění může také způsobit **návrhář tříd** má být vyvolána chyba **ve výběru nebyly nalezeny žádné typy**. Pokud narazíte na chyby, jako je tato, klikněte na tlačítko **zrušit** v chybové zprávě a čekání pro tento element kódu, než se objeví v **zobrazení tříd**. Jakmile to **návrhář tříd** měli být schopní zobrazit typu.

Pokud diagramu tříd neaktualizuje se změny provedené v kódu, možná budete muset diagram zavřít a znovu ho otevřete.

### <a name="type-resolution-issues"></a>Typ řešení problémů

**Třídy návrháře** nemusí být schopen převést typy z následujících důvodů:

- Typ je v projektu nebo sestavení, které není na něj odkazovat z projektu, který obsahuje diagramu tříd. Chcete-li opravit tuto chybu, přidejte odkaz na projekt nebo sestavení, které obsahuje typ. Další informace najdete v tématu [Správa odkazů v projektu](../managing-references-in-a-project.md).

- Typ není ve správném oboru, takže **návrhář tříd** nelze najít. Zkontrolujte, že kód není chybějící `using`, `imports`, nebo `#include` příkaz. Ujistěte se, že nebyly přesunut typ (nebo souvisejícího typu) mimo obor názvů, ve kterém byl původně nachází také.

- Typ neexistuje nebo byla změněna na komentář. A opravte tuto chybu, ujistěte se, že nejsou označené jako komentář nebo odstranit typ.

- Typ nachází v knihovně odkazuje #import – direktiva. Možných řešení je ručně přidat generovaný kód (soubor .tlh) #include – direktiva do záhlaví souboru.

- Ujistěte se, že **návrhář tříd** podporuje typ, který jste zadali. V tématu [omezení pro elementy kódu C++](#limitations-for-c-code-elements).

Chyba se nejpravděpodobněji najdete v části řešení problému typ je **kód nebyl nalezen pro jeden nebo více obrazců v diagramu tříd '\<element >'**. Tato chybová zpráva nemusí znamenat, že váš kód došlo k chybě. Znamená, že pouze tento návrhář tříd se nepodařilo zobrazení vašeho kódu. Zkuste následující míry:

- Zkontrolujte, zda typu. Zajistěte, aby mít není neúmyslně komentované a odstranit zdrojový kód.

- Došlo k pokusu o vyřešení typu. Typ může být v projektu nebo sestavení, které není na něj odkazovat z projektu, který obsahuje diagramu tříd. Chcete-li opravit tuto chybu, přidejte odkaz na projekt nebo sestavení, které obsahuje typ. Další informace najdete v tématu [Správa odkazů v projektu](../managing-references-in-a-project.md).

- Ujistěte se, že typ je ve správném oboru, aby ji mohli najít návrhář tříd. Ujistěte se, že kód není chybějící `using`, `imports`, nebo `#include` příkaz. Ujistěte se, že nebyly přesunut typ (nebo souvisejícího typu) mimo obor názvů, ve kterém byl původně nachází také.

### <a name="troubleshoot-other-error-messages"></a>Řešení potíží s další chybové zprávy

Pomoc při řešení potíží chyby a upozornění můžete najít ve veřejné fórech Microsoft Developer Network (MSDN). Najdete v článku [návrháře fórum sady Visual Studio – třída](http://go.microsoft.com/fwlink/?linkid=160754).

## <a name="limitations-for-c-code-elements"></a>Omezení pro elementy kódu C++

- Při načtení projektu Visual C++ **návrhář tříd** funguje způsobem, jen pro čtení. Můžete změnit diagramu tříd, ale nemůže uložit změny z diagramu tříd zpátky do zdrojového kódu.

- **Třídy návrháře** podporuje pouze nativní sémantiku C++. Pro projekty Visual C++, které jsou zkompilovány do spravovaného kódu **návrhář tříd** bude vizualizovat pouze elementy kódu, které jsou nativní typy. Proto můžete přidat diagramu tříd do projektu, ale **návrhář tříd** vám nedovolí vizualizovat elementy, ve kterém `IsManaged` je nastavena na `true` (to znamená, typů hodnot a odkazové typy).

- Pro projekty Visual C++ **návrhář tříd** čte pouze definici typu. Předpokládejme například, že můžete definovat typu v souboru hlavičky () a její členy v souboru implementace (sada). Pokud vyvolání "Zobrazení diagramu tříd" na soubor implementace (sada), **návrhář tříd** nic zobrazí. Jako další příklad – Pokud vyvolání "Zobrazení diagramu tříd" na sada souboru, který používá `#include` příkaz zahrnout další soubory, ale neobsahuje žádné skutečné – třída definice **návrhář tříd** znovu nic zobrazí.

- Soubory IDL (.idl), které definují rozhraní COM a knihovny typů, se nezobrazují v diagramech, pokud nejsou zkompilovány do nativního kódu C++.

- **Třídy návrháře** nepodporuje globální funkce a proměnné.

- **Třídy návrháře** nepodporuje sjednocení. Toto je zvláštní druh třída, ve které je paměť přidělená pouze množství potřebné pro Evropské unie největší datový člen.

- **Třídy návrháře** nezobrazí základní datové typy, jako `int` a `char`.

- **Třídy návrháře** nezobrazí typy, které jsou definovány mimo aktuální projekt, pokud projekt nemá správné odkazy na tyto typy.

- **Třídy návrháře** můžete zobrazit vnořené typy, ale není vztahy mezi vnořené typy a dalších typů.

- **Třídy návrháře** nelze zobrazit typy, které jsou neplatné nebo které jsou odvozeny od typu void.

## <a name="see-also"></a>Viz také

- [Navrhování a zobrazování tříd a typů](designing-and-viewing-classes-and-types.md)
- [Práce s diagramy tříd](working-with-class-diagrams.md)
- [Navrhování a zobrazování tříd a typů](designing-and-viewing-classes-and-types.md)
- [Další informace o chybách Návrháře tříd](additional-information-about-errors.md)
- [Třídy jazyka Visual C++ v Návrháři tříd](visual-cpp-classes.md)
- [Struktury jazyka Visual C++ v Návrháři tříd](visual-cpp-structures.md)
- [Výčty jazyka Visual C++ v Návrháři tříd](visual-cpp-enumerations.md)
- [Definice Typedefs jazyka Visual C++ v Návrháři tříd](visual-cpp-typedefs.md)
