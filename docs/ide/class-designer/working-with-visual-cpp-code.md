---
title: Práce s kódem C++ (Návrhář tříd)
description: Naučte se používat diagramy tříd pro návrh a vizualizaci prvku kódu C++, tříd a dalších typů v projektu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c3509f625686f97156efe79f5e1b72aa991ce5ca
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903881"
---
# <a name="work-with-c-code-in-class-designer"></a>Práce s kódem jazyka C++ v Návrhář tříd

**Návrhář tříd** zobrazuje vizuální návrhovou plochu nazvanou *Diagram tříd* , která poskytuje vizuální reprezentaci prvků kódu v projektu. Diagramy tříd můžete použít k návrhu a vizualizaci tříd a dalších typů v projektu.

**Návrhář tříd** podporuje následující prvky kódu jazyka C++:

- Třída (podobá se spravovanému tvaru třídy, s výjimkou toho, že může mít více vztahů dědičnosti)

- Anonymní třída (zobrazí Zobrazení tříd generovaný název anonymního typu.)

- Template – třída

- Struktura

- Výčet

- Makro (zobrazí zobrazení po zpracování v makru)

- Definic

> [!NOTE]
> To není stejné jako diagram třídy UML, který lze vytvořit v projektu modelování. Další informace najdete v tématu [diagramy tříd UML: Reference](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Řešení potíží s rozlišením typu a problémy se zobrazením

### <a name="location-of-source-files"></a>Umístění zdrojových souborů

**Návrhář tříd** nesleduje umístění zdrojových souborů. Proto pokud upravíte strukturu projektu nebo přesunete zdrojové soubory ve vašem projektu, **Návrhář tříd** může ztratit sledovat typ (zejména zdrojový typ typu typedef, základní třídy nebo typy přidružení). Může se zobrazit chyba, například **Návrhář tříd není možné zobrazit tento typ**. Pokud tak učiníte, znovu přetáhněte změněný nebo znovu umístěný zdrojový kód do diagramu tříd a znovu ho zobrazte.

### <a name="update-and-performance-issues"></a>Problémy s aktualizací a výkonem

Pro projekty v jazyce C++ může trvat 30 až 60 sekund, než se změna ve zdrojovém souboru objeví v diagramu tříd. Tato prodleva může také způsobit, **Návrhář tříd** vyvolat chybu. **ve výběru nebyly nalezeny žádné typy**. Pokud se zobrazí chyba, například, klikněte na tlačítko **Storno** v chybové zprávě a počkejte, než se element Code zobrazí v **zobrazení tříd**. Až to uděláte, **Návrhář tříd** by měl být schopný zobrazit typ.

Pokud diagram třídy neaktualizuje změny, které jste provedli v kódu, může být nutné diagram zavřít a znovu jej otevřít.

### <a name="type-resolution-issues"></a>Problémy s rozlišením typu

**Návrhář tříd** možná nebude možné přeložit typy z následujících důvodů:

- Typ je v projektu nebo sestavení, které není odkazováno z projektu, který obsahuje diagram třídy. Chcete-li opravit tuto chybu, přidejte odkaz na projekt nebo sestavení, které obsahuje daný typ. Další informace naleznete v tématu [Správa odkazů v projektu](../managing-references-in-a-project.md).

- Typ není ve správném rozsahu, takže ho **Návrhář tříd** nemůže najít. Ujistěte se, že v kódu chybí `using` příkaz, `imports` nebo `#include` . Také se ujistěte, že jste nepřesunuli typ (nebo související typ) mimo obor názvů, ve kterém byl původně umístěn.

- Typ neexistuje (nebo byl zakomentován). Chcete-li tuto chybu opravit, ujistěte se, že jste tento typ nepřidali nebo neodstranili.

- Typ se nachází v knihovně, na kterou odkazuje direktiva #import. Možným řešením je ruční přidání generovaného kódu (soubor. TLH) do direktivy #include do souboru hlaviček.

- Ujistěte se, že **Návrhář tříd** podporuje typ, který jste zadali. Viz [omezení pro prvky kódu jazyka C++](#limitations-for-c-code-elements).

Chyba, kterou nejčastěji vidíte pro problém s rozlišením typu, nebyl **nalezen pro jeden nebo více tvarů v diagramu tříd \<element>**. Tato chybová zpráva nemusí nutně znamenat, že váš kód je v chybovém prostředí. Označuje pouze to, že návrhář tříd nemůže zobrazit váš kód. Vyzkoušejte následující míry:

- Ujistěte se, že typ existuje. Ujistěte se, že jste neúmyslně zakomentováni nebo odstranili zdrojový kód.

- Zkuste typ vyřešit. Typ může být v projektu nebo sestavení, které není odkazováno z projektu, který obsahuje diagram třídy. Chcete-li opravit tuto chybu, přidejte odkaz na projekt nebo sestavení, které obsahuje daný typ. Další informace naleznete v tématu [Správa odkazů v projektu](../managing-references-in-a-project.md).

- Zajistěte, aby byl typ ve správném rozsahu, aby ho Návrhář tříd mohl najít. Ujistěte se, že v kódu chybí `using` `imports` příkaz, nebo `#include` . Také se ujistěte, že jste nepřesunuli typ (nebo související typ) mimo obor názvů, ve kterém byl původně umístěn.

### <a name="troubleshoot-other-error-messages"></a>Řešení potíží s jinými chybovými zprávami

Pomoc s chybami a upozorněními při řešení potíží najdete ve veřejných fórech MSDN (Microsoft Developer Network). Podívejte se na [Fórum sady Visual Studio Návrhář tříd](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner).

## <a name="limitations-for-c-code-elements"></a>Omezení pro prvky kódu C++

- Když je načten projekt jazyka C++, **Návrhář tříd** funkce pouze pro čtení. Můžete změnit diagram třídy, ale nemůžete uložit změny z diagramu tříd zpátky do zdrojového kódu.

- **Návrhář tříd** podporuje pouze nativní sémantiku jazyka C++. Pro projekty v jazyce C++, které jsou zkompilovány do spravovaného kódu, **Návrhář tříd** budou vizualizovat pouze prvky kódu, které jsou nativní typy. Proto můžete přidat diagram tříd do projektu, ale **Návrhář tříd** neumožní vizualizovat prvky, ve kterých `IsManaged` je vlastnost nastavena na `true` (tj. typy hodnot a odkazové typy).

- Pro projekty v jazyce C++ **Návrhář tříd** čte pouze definici typu. Předpokládejme například, že definujete typ v souboru hlaviček (. h) a definujete jeho členy v implementačním souboru (. cpp). Pokud vyvoláte "Zobrazit diagram tříd" v implementačním souboru (. cpp), **Návrhář tříd** nezobrazí nic. Další příklad: Pokud vyvoláte "Zobrazit diagram tříd" na souboru. cpp, který používá `#include` příkaz pro zahrnutí jiných souborů, ale neobsahuje žádné skutečné definice třídy, **Návrhář tříd** znovu nezobrazí nic.

- Soubory IDL (. idl), které definují rozhraní COM a knihovny typů, se nezobrazují v diagramech, pokud nejsou kompilovány do nativního kódu jazyka C++.

- **Návrhář tříd** nepodporuje globální funkce a proměnné.

- **Návrhář tříd** nepodporuje sjednocení. Toto je speciální typ třídy, ve které je přidělená paměť pouze ta, která je potřebná pro největší datový člen sjednocení.

- **Návrhář tříd** nezobrazuje základní datové typy, například `int` a `char` .

- **Návrhář tříd** nezobrazuje typy, které jsou definovány mimo aktuální projekt, pokud projekt nemá správné odkazy na tyto typy.

- **Návrhář tříd** může zobrazit vnořené typy, ale ne vztahy mezi vnořeným typem a dalšími typy.

- **Návrhář tříd** nemůže zobrazit typy, které jsou anulovány nebo odvozeny od typu void.

## <a name="see-also"></a>Viz také

- [Navrhování a zobrazování tříd a typů](designing-and-viewing-classes-and-types.md)
- [Další informace o chybách Návrháře tříd](additional-information-about-errors.md)
- [Třídy jazyka C++ v Návrhář tříd](visual-cpp-classes.md)
- [Struktury C++ v Návrhář tříd](visual-cpp-structures.md)
- [Výčty C++ v Návrhář tříd](visual-cpp-enumerations.md)
- [Definice typedef C++ v Návrhář tříd](visual-cpp-typedefs.md)
