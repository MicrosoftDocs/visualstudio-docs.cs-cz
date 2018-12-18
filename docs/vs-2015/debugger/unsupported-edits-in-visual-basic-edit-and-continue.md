---
title: Nepodporované úpravy v jazyce Visual Basic operaci upravit a pokračovat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc6e7a5d1d72464849bff20be066ea70e8264623
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787897"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Nepodporované úpravy v operaci Upravit a pokračovat jazyka Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upravit a pokračovat les zastaví spuštění programu v režimu pozastavení, provést změny provádění kódu a pokračovat v provádění programu s nově zahrnutých změny. Úpravy deklarativního kódu, které ovlivňují Veřejná struktura třídy jsou obecně zakázáno, ale mnoho úpravy, které můžete provést metoda, vlastnost text nebo privátní deklarace v rámci třídy jsou povoleny.  
  
 Pokud je potřeba provést změnu, která není podporována, musíte Zastavit ladění, proveďte požadované změny a spuštění nové ladicí relace.  
  
###  <a name="BKMK_MethodandPropertyBodyEdits"></a> Metody a vlastnosti úpravy textu  
 **Nepodporované změny statické lokální proměnné**: Přidání nebo aktualizace místní proměnné nebo odebrání statické místní proměnné, pokud by to způsobilo chybu kompilace.  
  
 **Nepodporované změny do obecných typů**: změny obecný samotnou metodu nebo obecné metody textu nejsou podporovány. Vytváření instancí obecného typu nebo volání na existující obecné metody lze přidat, odstranit nebo změnit.  
  
 **Ostatní nepodporované změny**  
  
-   Změna příkazu volání metody, která je v zásobníku volání.  
  
-   Přidávání `Try...Catch` blok, když ukazatele na instrukci končí v `Catch` bloku nebo `Finally` bloku.  
  
-   Odebrání `Try...Catch` blok, když je ukazatel instrukce v `Catch`bloku nebo `Finally` bloku.  
  
-   Přidání `Using` bloku kolem aktuálního ukazatele na instrukci.  
  
-   Přidání `SynchLock` bloku kolem aktuálního ukazatele na instrukci.  
  
###  <a name="BKMK_AttributeEdits"></a> Úpravy atributu  
 Upravit a pokračovat nepodporuje změny atributů. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Definování, úprava nebo odstranění třídu atributu.  
  
-   Přidání atributu.  
  
-   Úpravy nebo odstranění existující atribut.  
  
###  <a name="BKMK_ClassDeclarationEdits"></a> Úpravy deklarace třídy  
 Většina změn deklarací třídy nejsou povoleny funkce upravit a pokračovat v režimu přerušení. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Přejmenování, odstranění nebo změna dědičnosti existující třídy.  
  
-   Implementace nové rozhraní nebo odebrání implementaci rozhraní.  
  
-   Změna modifikátory třídy.  
  
-   Přidání, změně nebo odebrání `ComClass` stav.  
  
-   Úpravy všechny deklarace obecných tříd.  
  
###  <a name="BKMK_ClassMemberDeclarationEdits"></a> Úpravy deklarace člena třídy  
 Změny deklarace členů jsou zakázány ve většině upravit a pokračovat v případech. Například nemůžete změnit podpis nebo úroveň přístupu členem, a pokud nemůžete odebrat úplně členy, které způsobí chybu kompilace. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Stínový provoz existující členskou proměnnou deklarováním globální nebo členské proměnné se stejným názvem v bloku.  
  
-   Stínový provoz statické místní proměnné deklarováním novou instanci uvnitř bloku.  
  
-   Odebírání obslužných rutin události. Přidání obslužné rutiny události je povoleno.  
  
-   Přidání nové přetížení vlastnosti nebo metody, pokud vlastnost nebo metoda je `Private` a neexistují žádné výskyty názvu v žádné aktivní příkaz.  
  
-   Přidání nebo odebrání `WithEvents` klauzuli členské proměnné.  
  
-   Odstraňuje se členem.  
  
-   Změna deklaraci vlastnosti nebo metody zastavit implementace rozhraní.  
  
-   Úpravy jakoukoli metodu, která používá obecné typy.  
  
-   Změna podpisu nebo návratový typ veřejné vlastnosti nebo metody.  
  
-   Přepsání nebo stínováním členem v základní třídě.  
  
-   Přidání nového pole v libovolné třídě označené `SequentialLayout` nebo `ExplicitLayout`.  
  
-   Změna `MustInherit` nebo `NotOverridable` stav metody.  
  
-   Změna přístupu modifikátory přístupu pro vlastnosti nebo metody.  
  
-   Změna typu nebo jen pro čtení stavu pole.  
  
-   Změna veřejné pole.  
  
###  <a name="BKMK_CompilerOptionEdits"></a> Úpravy – možnost kompilátoru  
 Při použití funkce upravit a pokračovat v režimu přerušení, nelze změnit, přidat nebo odebrat následující možnosti kompilátoru:  
  
-   **Možnost Strict**  
  
-   **Možnost Explicit**  
  
-   **Možnost Compare**  
  
###  <a name="BKMK_ConstantsEdits"></a> Úpravy konstanty  
 Změny v režimu Edit and Continue konstanty jsou velmi omezená. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Přidání nebo aktualizace konstantní proměnné.  
  
-   Změna typem nebo hodnotou konstanty.  
  
-   Odebrání konstantu.  
  
###  <a name="BKMK_DelegateandEventDeclarationEdits"></a> Delegát a úpravy deklarace událostí  
 Některé změny Delegáti a události nejsou povoleny funkce upravit a pokračovat během režimu pozastavení. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Změna nebo odstranění definice delegáta.  
  
-   Odstraňuje se události.  
  
###  <a name="BKMK_EnumerationEdits"></a> Výčet úpravy  
 Změní na výčty (`Enums`) nejsou povoleny funkce upravit a pokračovat v režimu přerušení. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Změna základního typu `Enum`.  
  
-   Přidání, změně nebo odebrání `Enum` člena.  
  
-   Změna modifikátor přístupu `Enum`.  
  
###  <a name="BKMK_ExternalDeclarationsEdits"></a> Externí deklarace úpravy  
 Deklarace externí metody obecně nelze změnit během příkazu upravit a pokračovat. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Přidání nebo odebrání externí deklarace.  
  
-   Změna podpisu nebo zařazování atributy externí deklarace.  
  
###  <a name="BKMK_ImportsEdits"></a> Importuje úpravy  
 Upravit a pokračovat neumožňuje přidání, změně nebo odebrání `Imports` příkazy v režimu přerušení.  
  
###  <a name="BKMK_InterfaceDefinitionEdits"></a> Úpravy definice rozhraní  
 I když jsou často může provádět změny členů, které implementují rozhraní, změny v definicích skutečné rozhraní nejsou obecně povoleny funkce upravit a pokračovat. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Přidání, změně nebo odebrání členů rozhraní.  
  
-   Odstraňuje se existující rozhraní.  
  
-   Změna modifikátor přístupu rozhraní.  
  
-   Změna rozhraní hierarchii dědičnosti.  
  
###  <a name="BKMK_ModuleDeclarationEdits"></a> Úpravy deklarace modulu  
 Většina změn deklarace modulů nejsou povoleny funkce upravit a pokračovat v režimu přerušení. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Vytváří se nový modul.  
  
-   Přejmenování nebo odstranění existující modul.  
  
-   Změna modifikátor přístupu pro modul.  
  
###  <a name="BKMK_ModuleMemberDeclarationEdits"></a> Úpravy deklarace člena modulu  
 Použitím funkce upravit a pokračovat, můžete provést řadu změn modulu členy, jako jsou vlastnosti, metody a pole, v režimu přerušení. Nicméně některé změny nejsou podporovány. Zejména, upravit a pokračovat nepodporuje přidání, odstranění nebo změna typu nebo podpis žádné členy.  
  
 Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Pokud neexistují žádné výskyty názvu v jakékoli aktivního příkazu přidáte nového člena.  
  
-   Odebrání vlastnosti nebo metody.  
  
-   Změna podpisu vlastnosti nebo metody.  
  
-   Přidání, přejmenování, přesunutí nebo odstranění pole.  
  
-   Úpravy jakoukoli metodu, která používá obecné typy.  
  
-   Změna přístupu modifikátory přístupu pro vlastnosti nebo metody, například změna `Public` k `Private`.  
  
-   Odstranění nebo změna typu existujícího pole.  
  
###  <a name="BKMK_NestedTypeDeclarationEdits"></a> Vnořený typ deklarace úpravy  
 Upravit a pokračovat nepodporuje přechod na jiný obor názvů nebo typ vnořeného typu.  
  
###  <a name="BKMK_StructureDeclarationEdits"></a> Úpravy deklarace struktury  
 Většina změn deklarace struktur nejsou povoleny funkce upravit a pokračovat při v **přerušit** režimu. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Přejmenování nebo odstranění existující strukturu.  
  
-   Implementace nové rozhraní nebo odebrání implementaci rozhraní.  
  
-   Změna modifikátor přístupu pro strukturu.  
  
###  <a name="BKMK_StructureMemberDeclarationEdits"></a> Úpravy deklarace člena struktury  
 Použitím funkce upravit a pokračovat, můžete provést řadu změn členy struktury (vlastnosti, metody a pole) při v režimu pozastavení. Některé změny, ale podporované nejsou, zejména změny, které mají vliv deklarace členy struktury. Konkrétně, upravit a pokračovat nepodporuje následující změny:  
  
-   Odebrání vlastnosti nebo metody.  
  
-   Přidání nebo odebrání pole.  
  
-   Změna podpisu vlastnosti nebo metody.  
  
-   Úpravy jakoukoli metodu, která používá obecné typy.  
  
-   Změna, ať už se implementuje rozhraní deklaraci vlastnosti nebo metody.  
  
-   Změna vlastnosti nebo metody přístupu modifikátory přístupu (například změna `Public` k **privátní**).  
  
-   Odebrání pole.  
  
-   Změna typu pole.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití úprav v režimu pozastavení pomocí operace upravit a pokračovat](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Upravit a pokračovat (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



