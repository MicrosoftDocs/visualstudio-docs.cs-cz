---
title: Práce s kódem Jazyka C++ (Návrhář tříd)
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- C++, Class Designer
- Class Designer, C++ support
- Class Designer, limitations
- Class Designer, tasks in C++
- C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 54087a719b0079ba32ff08ff1e08ad01f5e64ed0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596746"
---
# <a name="work-with-c-code-in-class-designer"></a>Práce s kódem C++ v Návrháři tříd

**Návrhář tříd** zobrazuje vizuální návrhový povrch nazývaný *diagram třídy,* který poskytuje vizuální reprezentaci prvků kódu v projektu. Diagramy tříd můžete použít k návrhu a vizualizaci tříd a dalších typů v projektu.

**Návrhář tříd** podporuje následující prvky kódu jazyka C++:

- Třída (podobá se obrazci spravované třídy s tím rozdílem, že může mít více vztahů dědičnosti)

- Anonymní třída (zobrazí generovaný název zobrazení třídy pro anonymní typ)

- Třída Šablony

- Struktura

- Výčet

- Makro (zobrazí pohled makra po zpracování)

- Typedef

> [!NOTE]
> To není stejné jako diagram třídy UML, který můžete vytvořit v projektu modelování. Další informace naleznete [v tématu Diagramy tříd UML: Reference](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Poradce při potížích s překladem typů a zobrazením

### <a name="location-of-source-files"></a>Umístění zdrojových souborů

**Návrhář třídne** nesleduje umístění zdrojových souborů. Proto pokud změníte strukturu projektu nebo přesunout zdrojové soubory v projektu, **Návrhář třídy** může ztratit přehled o typu (zejména typ zdroje typedef, základní třídy nebo typy přidružení). Může se zobrazit chyba, například **Návrhář tříd nemůže zobrazit tento typ**. Pokud tak učiníte, přetáhněte upravený nebo přemístěný zdrojový kód do diagramu třídy znovu zobrazit.

### <a name="update-and-performance-issues"></a>Problémy s aktualizací a výkonem

U projektů jazyka C++ může trvat 30 až 60 sekund, než se změna zdrojového souboru zobrazí v diagramu třídy. Toto zpoždění může také způsobit **Návrhář e-taky** vyvolat chybu **Žádné typy byly nalezeny ve výběru**. Pokud se zobrazí chyba, jako je tato, klepněte na tlačítko **Storno** v chybové zprávě a počkejte, až se prvek kódu zobrazí v **zobrazení třídy**. Poté by měl být **návrhář tříd** schopen zobrazit typ.

Pokud diagram třídy neaktualizuje se změnami, které jste provedli v kódu, bude pravděpodobně nutné zavřít diagram a znovu jej otevřít.

### <a name="type-resolution-issues"></a>Problémy s překladem typů

**Návrhář tříd** nemusí být schopen vyřešit typy z následujících důvodů:

- Typ je v projektu nebo sestavení, který není odkazován z projektu, který obsahuje diagram třídy. Chcete-li tuto chybu opravit, přidejte odkaz na projekt nebo sestavení, které obsahuje typ. Další informace naleznete [v tématu Správa odkazů v projektu](../managing-references-in-a-project.md).

- Typ není ve správném oboru, takže **Návrhář třídy jej** nemůže najít. Ujistěte se, že `using`kód `imports`nechybí , , nebo `#include` příkaz. Také se ujistěte, že jste nepřesunuli typ (nebo související typ) z oboru názvů, ve kterém byl původně umístěn.

- Typ neexistuje (nebo byl zakomentován). Chcete-li tuto chybu opravit, ujistěte se, že jste typ nekomentovali ani neodstranili.

- Typ je umístěn v knihovně odkazuje #import směrnice. Možným zástupným řešení je ruční přidání generovaného kódu (souboru TLH) do direktivy #include do souboru záhlaví.

- Ujistěte se, že **Návrhář tříd** podporuje typ, který jste zadali. Viz [Omezení pro prvky kódu jazyka C++](#limitations-for-c-code-elements).

Chyba, kterou s největší pravděpodobností uvidíte u problému s překladem **typů, je,\<že kód nebyl nalezen pro jeden nebo více obrazců v diagramu třídy " element> '**. Tato chybová zpráva nemusí nutně znamenat, že váš kód je v chybě. Označuje pouze, že návrhář třídy nemohl zobrazit váš kód. Vyzkoušejte následující opatření:

- Ujistěte se, že typ existuje. Ujistěte se, že jste neúmyslně nekomentovali nebo neodstranili zdrojový kód.

- Pokuste se přeložit typ. Typ může být v projektu nebo sestavení, který není odkazován z projektu, který obsahuje diagram třídy. Chcete-li tuto chybu opravit, přidejte odkaz na projekt nebo sestavení, které obsahuje typ. Další informace naleznete [v tématu Správa odkazů v projektu](../managing-references-in-a-project.md).

- Ujistěte se, že typ je ve správném oboru tak, aby Návrhář třídy můžete vyhledat. Ujistěte se, že kód `using` `imports`nechybí `#include` , , nebo příkaz. Také se ujistěte, že jste nepřesunuli typ (nebo související typ) z oboru názvů, ve kterém byl původně umístěn.

### <a name="troubleshoot-other-error-messages"></a>Poradce při potížích s dalšími chybovými zprávami

Pomoc s odstraňováním chyb a upozornění naleznete ve veřejných fórech služby Microsoft Developer Network (MSDN). Podívejte se na [Fórum návrháře tříd visual studia](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner).

## <a name="limitations-for-c-code-elements"></a>Omezení pro prvky kódu jazyka C++

- Při načtení projektu Jazyka C++ **funkce Návrhář e-class** způsobem. Diagram třídy můžete změnit, ale změny z diagramu třídy nelze uložit zpět do zdrojového kódu.

- **Návrhář tříd** podporuje pouze nativní sémantiku jazyka C++. Pro projekty jazyka C++, které jsou kompilovány do spravovaného kódu, **návrhář tříd** y vizualizovat pouze prvky kódu, které jsou nativní typy. Proto můžete přidat diagram třídy do projektu, ale **Návrhář tříd** neumožňuje vizualizovat prvky, ve kterých je `IsManaged` vlastnost nastavena `true` (to znamená, že typy hodnot a typy odkazů).

- Pro projekty jazyka C++ **návrhář třídy** čte pouze definici typu. Předpokládejme například, že definujete typ v souboru záhlaví (.h) a definujete jeho členy v souboru implementace (.cpp). Pokud vyvoláte "Zobrazit diagram tříd" v souboru implementace (.cpp), **Návrhář tříd** nezobrazí nic. Jako další příklad, pokud vyvoláte "Zobrazit diagram tříd" v `#include` souboru CPP, který používá příkaz zahrnout další soubory, ale neobsahuje žádné skutečné definice tříd, **Návrhář tříd** znovu nezobrazí nic.

- Soubory IDL (.idl), které definují rozhraní MODELU COM a knihovny typů, se nezobrazují v diagramech, pokud nejsou zkompilovány do nativního kódu Jazyka C++.

- **Návrhář třídne** nepodporuje globální funkce a proměnné.

- **Návrhář třídy** nepodporuje sjednocení. Toto je zvláštní typ třídy, ve kterém přidělené paměti je pouze částka potřebná pro největší datový člen unie.

- **Návrhář tříd nezobrazuje** základní datové `int` `char`typy, jako jsou například a .

- **Návrhář třídy** nezobrazuje typy, které jsou definovány mimo aktuální projekt, pokud projekt nemá správné odkazy na tyto typy.

- **Návrhář tříd může** zobrazit vnořené typy, ale ne vztahy mezi vnořený typ a jiné typy.

- **Návrhář třídy** nemůže zobrazit typy, které jsou neplatné nebo které jsou odvozeny z typu void.

## <a name="see-also"></a>Viz také

- [Navrhování a zobrazování tříd a typů](designing-and-viewing-classes-and-types.md)
- [Další informace o chybách Návrháře tříd](additional-information-about-errors.md)
- [Třídy C++ v Návrháři tříd](visual-cpp-classes.md)
- [Struktury Jazyka C++ v návrháři tříd](visual-cpp-structures.md)
- [Výčty jazyka C++ v Návrháři tříd](visual-cpp-enumerations.md)
- [C++ Typedefs v Návrháři tříd](visual-cpp-typedefs.md)
