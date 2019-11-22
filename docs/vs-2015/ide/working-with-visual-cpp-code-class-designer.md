---
title: Práce s vizuálním C++ kódem (návrhář tříd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb2b5a55f778b8025ea9da25713eca903f9cbf74
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296218"
---
# <a name="working-with-visual-c-code-class-designer"></a>Práce s kódem jazyka Visual C++ (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návrhář tříd zobrazuje vizuální návrhovou plochu nazvanou *Diagram tříd* , která poskytuje vizuální reprezentaci prvků kódu v projektu. Diagramy tříd můžete použít k návrhu a vizualizaci tříd a dalších typů v projektu.

 Návrhář tříd podporuje následující C++ prvky kódu:

- Třída (podobá se spravovanému tvaru třídy, s výjimkou toho, že může mít více vztahů dědičnosti)

- Anonymní třída (zobrazí Zobrazení tříd generovaný název anonymního typu.)

- Template – třída

- Struktura

- Enum

- Makro (zobrazí zobrazení po zpracování v makru)

- Definic

> [!NOTE]
> To není stejné jako diagram třídy UML, který lze vytvořit v projektu modelování. Další informace najdete v tématu [diagramy tříd UML: Reference](../modeling/uml-class-diagrams-reference.md).

## <a name="troubleshooting-type-resolution-and-display-issues"></a>Řešení potíží s rozlišením typu a problémy se zobrazením

### <a name="location-of-source-files"></a>Umístění zdrojových souborů
 Návrhář tříd nesleduje umístění zdrojových souborů. Proto pokud upravíte strukturu projektu nebo přesunete zdrojové soubory ve vašem projektu, Návrhář tříd může ztratit sledovat typ (zejména zdrojový typ typu typedef, základní třídy nebo typy přidružení). Může se zobrazit chyba, například **Návrhář tříd není možné zobrazit tento typ**. Pokud tak učiníte, znovu přetáhněte změněný nebo znovu umístěný zdrojový kód do diagramu tříd a znovu ho zobrazte.

### <a name="update-and-performance-issues"></a>Problémy s aktualizací a výkonem
 U vizuálních C++ projektů může trvat 30 až 60 sekund, než se změna ve zdrojovém souboru objeví v diagramu tříd. Tato prodleva může také způsobit, Návrhář tříd vyvolat chybu. **ve výběru nebyly nalezeny žádné typy**. Pokud se zobrazí chyba, například, klikněte na tlačítko **Storno** v chybové zprávě a počkejte, než se element Code zobrazí v zobrazení tříd. Až to uděláte, Návrhář tříd by měl být schopný zobrazit typ.

 Pokud diagram třídy neaktualizuje změny, které jste provedli v kódu, může být nutné diagram zavřít a znovu jej otevřít.

### <a name="type-resolution-issues"></a>Problémy s rozlišením typu
 Návrhář tříd možná nebude možné přeložit typy z následujících důvodů:

- Typ je v projektu nebo sestavení, které není odkazováno z projektu, který obsahuje diagram třídy. Chcete-li opravit tuto chybu, přidejte odkaz na projekt nebo sestavení, které obsahuje daný typ. Další informace naleznete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Typ není ve správném rozsahu, takže ho Návrhář tříd nemůže najít. Ujistěte se, že v kódu chybí příkaz `using`, `imports`nebo `#include`. Také se ujistěte, že jste nepřesunuli typ (nebo související typ) mimo obor názvů, ve kterém byl původně umístěn.

- Typ neexistuje (nebo byl zakomentován). Chcete-li tuto chybu opravit, ujistěte se, že jste tento typ nepřidali nebo neodstranili.

- Typ se nachází v knihovně, na kterou odkazuje direktiva #import. Možným řešením je ruční přidání generovaného kódu (soubor. TLH) do direktivy #include do souboru hlaviček.

  Chyba, kterou nejčastěji vidíte pro problém s rozlišením typu, nebyl **nalezen v jednom nebo více tvarech v diagramu tříd '\<elementu > '** . Tato chybová zpráva nemusí nutně znamenat, že váš kód je v chybovém prostředí. Označuje pouze to, že návrhář tříd nemůže zobrazit váš kód. Vyzkoušejte následující míry.

- Ujistěte se, že typ existuje. Ujistěte se, že jste neúmyslně zakomentováni nebo odstranili zdrojový kód.

- Ujistěte se, že Návrhář tříd podporuje typ, který jste zadali. Viz [omezení pro C++ prvky kódu](#limitations).

- Zkuste typ vyřešit. Typ může být v projektu nebo sestavení, které není odkazováno z projektu, který obsahuje diagram třídy. Chcete-li opravit tuto chybu, přidejte odkaz na projekt nebo sestavení, které obsahuje daný typ. Další informace naleznete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Zajistěte, aby byl typ ve správném rozsahu, aby ho Návrhář tříd mohl najít. Ujistěte se, že v kódu chybí příkaz `using`, `imports`nebo `#include`. Také se ujistěte, že jste nepřesunuli typ (nebo související typ) mimo obor názvů, ve kterém byl původně umístěn.

### <a name="troubleshooting-other-error-messages"></a>Řešení potíží s jinými chybovými zprávami
 Pomoc s chybami a upozorněními při řešení potíží najdete ve veřejných fórech MSDN (Microsoft Developer Network). Podívejte se na [Fórum sady Visual Studio Návrhář tříd](https://go.microsoft.com/fwlink/?linkid=160754).

## <a name="limitations"></a>Omezení pro C++ prvky kódu

- Při načtení vizuálního C++ projektu Návrhář tříd funkce způsobem jen pro čtení. Můžete změnit diagram třídy, ale nemůžete uložit změny z diagramu tříd zpátky do zdrojového kódu.

- Návrhář tříd podporuje pouze nativní C++ sémantiku. V případě C++ vizuálních projektů, které jsou zkompilovány do spravovaného kódu, návrhář tříd bude vizualizovat pouze prvky kódu, které jsou nativní typy. Proto můžete přidat diagram tříd do projektu, ale Návrhář tříd neumožní vizualizovat prvky, ve kterých je vlastnost `IsManaged` nastavena na `true` (tj. typy hodnot a odkazové typy).

- V případě C++ vizuálních projektů Návrhář tříd čte pouze definici typu. Předpokládejme například, že definujete typ v souboru hlaviček (. h) a definujete jeho členy v implementačním souboru (. cpp). Pokud vyvoláte "Zobrazit diagram tříd" v implementačním souboru (. cpp), Návrhář tříd nezobrazí nic. Další příklad: Pokud vyvoláte "Zobrazit diagram tříd" na souboru. cpp, který používá příkaz `#include` pro zahrnutí jiných souborů, ale neobsahuje žádné skutečné definice třídy, Návrhář tříd znovu nezobrazí nic.

- IDL (. idl) soubory, které definují rozhraní COM a knihovny typů, se nezobrazují v diagramech, pokud nejsou zkompilovány do nativního C++ kódu.

- Návrhář tříd nepodporuje globální funkce a proměnné.

- Návrhář tříd nepodporuje sjednocení. Toto je speciální typ třídy, ve které je přidělená paměť pouze ta, která je potřebná pro největší datový člen sjednocení.

- Návrhář tříd nezobrazuje základní datové typy, například `int` a `char`.

- Návrhář tříd nezobrazuje typy, které jsou definovány mimo aktuální projekt, pokud projekt nemá správné odkazy na tyto typy.

- Návrhář tříd může zobrazit vnořené typy, ale ne vztahy mezi vnořeným typem a dalšími typy.

- Návrhář tříd nemůže zobrazit typy, které jsou anulovány nebo odvozeny od typu void.

## <a name="see-also"></a>Viz také
 [Navrhování a zobrazování tříd a typů](../ide/designing-and-viewing-classes-and-types.md) [pracujících s třídami a jinými typy (návrhář tříd)](../ide/working-with-classes-and-other-types-class-designer.md) [práce s diagramy tříd (návrhář tříd)](../ide/working-with-class-diagrams-class-designer.md) [navrhování tříd a typů (návrhář tříd)](../ide/designing-classes-and-types-class-designer.md) [Další informace o Návrhář třídch](../ide/additional-information-about-class-designer-errors.md) [ C++ vizuálních třídách chyb v](../ide/visual-cpp-classes-in-class-designer.md) [ C++ Návrhář tříd](../ide/visual-cpp-structures-in-class-designer.md) vizuálních [ C++ výčtech](../ide/visual-cpp-enumerations-in-class-designer.md) v Návrhář tříd vizuálních výčtech v Návrhář tříd Visual [ C++ definice typedef v](../ide/visual-cpp-typedefs-in-class-designer.md) Návrhář tříd
