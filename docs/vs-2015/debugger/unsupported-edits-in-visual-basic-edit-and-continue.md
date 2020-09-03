---
title: Nepodporované úpravy v Visual Basic upravit a pokračovat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 94a151a7adab5c8246cec38c2e62d76788beb6e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155437"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Nepodporované úpravy v operaci Upravit a pokračovat jazyka Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upravit a pokračovat: Les zastavíte provádění programu v režimu pozastavení, provedete změny spuštěného kódu a obnovíte provádění programu s nově začleněnými změnami. Deklarativní úpravy kódu, které mají vliv na veřejnou strukturu třídy, jsou obecně zakázané, ale mnoho úprav, které lze provést v metodě, tělo vlastnosti nebo soukromé deklarace v rámci třídy, jsou povoleny.  
  
 Pokud potřebujete provést změnu, která není podporována, je nutné zastavit ladění, provést změny a spustit novou relaci ladění.  
  
### <a name="method-and-property-body-edits"></a><a name="BKMK_MethodandPropertyBodyEdits"></a> Úpravy textu metody a vlastností  
 **Nepodporované změny statických lokálních proměnných**: Přidání nebo aktualizace místní proměnné nebo odebrání statické lokální proměnné, pokud by to způsobilo chybu kompilace.  
  
 **Nepodporované změny obecných typů**: změny samotné obecné metody nebo těla obecné metody nejsou podporovány. Instance obecného typu nebo volání existující obecné metody lze přidat, odstranit nebo změnit.  
  
 **Jiné nepodporované změny**  
  
- Změna příkazu vyvolání metody, která je v zásobníku volání.  
  
- Přidání `Try...Catch` bloku, když ukazatel na instrukci skončí v `Catch` bloku nebo `Finally` bloku.  
  
- Odebrání `Try...Catch` bloku, pokud je ukazatel instrukcí v `Catch` bloku nebo `Finally` bloku.  
  
- Přidání `Using` bloku kolem aktuálního ukazatele instrukcí.  
  
- Přidání `SynchLock` bloku kolem aktuálního ukazatele instrukcí.  
  
### <a name="attribute-edits"></a><a name="BKMK_AttributeEdits"></a> Úpravy atributů  
 Upravit a pokračovat nepodporuje úpravu atributů. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Definování, úprava nebo odstranění třídy atributů.  
  
- Přidání atributu.  
  
- Úpravy nebo odebrání existujícího atributu.  
  
### <a name="class-declaration-edits"></a><a name="BKMK_ClassDeclarationEdits"></a> Úpravy deklarace třídy  
 Většina změn v deklaracích třídy není povolená v režimu pozastavení v době úprav a pokračování. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Přejmenování, odstranění nebo změna dědičnosti existující třídy.  
  
- Implementace nového rozhraní nebo odebrání implementace rozhraní.  
  
- Změna modifikátorů u třídy.  
  
- Přidání, změna nebo odebrání `ComClass` stavu.  
  
- Úprava libovolné deklarace obecné třídy.  
  
### <a name="class-member-declaration-edits"></a><a name="BKMK_ClassMemberDeclarationEdits"></a> Úpravy deklarace členů třídy  
 Změny deklarací členů jsou ve většině případů úprav a pokračování zakázané. Například nemůžete změnit signaturu nebo úroveň přístupu člena a nemůžete kompletně odebrat členy, pokud by to způsobilo chybu při kompilaci. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Nastínování existující členské proměnné deklarováním globální nebo členské proměnné se stejným názvem v bloku, který ho obsahuje.  
  
- Nastínování statické místní proměnné deklarováním nové instance uvnitř bloku.  
  
- Odebírání obslužných rutin pro událost. Přidání obslužné rutiny události je povoleno.  
  
- Přidání nové přetížené vlastnosti nebo metody, pokud není vlastnost nebo metoda `Private` a v žádném aktivním příkazu nejsou žádné výskyty názvu.  
  
- Přidání nebo odebrání `WithEvents` klauzule na členské proměnné.  
  
- Odstranění člena.  
  
- Změna deklarace vlastnosti nebo metody k zastavení implementace rozhraní.  
  
- Úprava libovolné metody, která používá obecné typy.  
  
- Změna podpisu nebo návratového typu neprivátní vlastnosti nebo metody.  
  
- Přepisování nebo stínování člena v základní třídě.  
  
- Přidání nového pole v jakékoli třídě označené `SequentialLayout` nebo `ExplicitLayout` .  
  
- Změna `MustInherit` `NotOverridable` stavu metody nebo.  
  
- Změna modifikátorů přístupu pro vlastnost nebo metodu.  
  
- Změna typu nebo stavu pouze pro čtení v poli.  
  
- Změna veřejného pole.  
  
### <a name="compiler-option-edits"></a><a name="BKMK_CompilerOptionEdits"></a> Úpravy možností kompilátoru  
 Při použití možnosti upravit a pokračovat v režimu pozastavení nelze změnit, přidat nebo odebrat následující možnosti kompilátoru:  
  
- **Možnost Strict**  
  
- **Možnost Explicit**  
  
- **Možnost Compare**  
  
### <a name="constants-edits"></a><a name="BKMK_ConstantsEdits"></a> Úpravy konstant  
 Změny konstant v režimu úprav a pokračování jsou velmi omezené. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Přidání nebo aktualizace konstantní proměnné.  
  
- Změna typu nebo hodnoty konstanty.  
  
- Odebírá se konstanta.  
  
### <a name="delegate-and-event-declaration-edits"></a><a name="BKMK_DelegateandEventDeclarationEdits"></a> Úpravy deklarace delegáta a události  
 Některé změny delegátů a událostí nejsou povoleny úpravou a pokračováním během režimu přerušení. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Změna nebo odstranění definice delegáta.  
  
- Odstraňování události  
  
### <a name="enumeration-edits"></a><a name="BKMK_EnumerationEdits"></a> Úpravy výčtu  
 Změny výčtů ( `Enums` ) nejsou povoleny úpravou a pokračováním během režimu přerušení. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Úprava základního typu `Enum` .  
  
- Přidání, změna nebo odebrání `Enum` člena.  
  
- Změna modifikátoru přístupu pro `Enum` .  
  
### <a name="external-declarations-edits"></a><a name="BKMK_ExternalDeclarationsEdits"></a> Úpravy externích deklarací  
 Obecně platí, že během úprav a pokračování nelze deklarace externích metod změnit. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Přidání nebo odebrání externí deklarace.  
  
- Změna podpisu nebo zařazování atributů vnější deklarace.  
  
### <a name="imports-edits"></a><a name="BKMK_ImportsEdits"></a> Import úprav  
 Příkaz Upravit a pokračovat neumožňuje přidávat, měnit ani odebírat `Imports` příkazy v režimu přerušení.  
  
### <a name="interface-definition-edits"></a><a name="BKMK_InterfaceDefinitionEdits"></a> Úpravy definic rozhraní  
 I když je často povoleno provádět změny členů, kteří implementují rozhraní, nejsou změny v skutečných definicích rozhraní obecně povoleny úpravou a pokračováním. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Přidání, změna nebo odebrání členů rozhraní.  
  
- Odstraňuje se existující rozhraní.  
  
- Změna modifikátoru přístupu rozhraní.  
  
- Změna Hierarchie dědičnosti rozhraní.  
  
### <a name="module-declaration-edits"></a><a name="BKMK_ModuleDeclarationEdits"></a> Úpravy deklarací modulů  
 Většina změn v deklaracích modulů není povolená v režimu pozastavení v době úprav a pokračování. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Vytváří se nový modul.  
  
- Přejmenování nebo odstranění existujícího modulu.  
  
- Změna modifikátoru přístupu pro modul.  
  
### <a name="module-member-declaration-edits"></a><a name="BKMK_ModuleMemberDeclarationEdits"></a> Úpravy deklarace člena modulu  
 Pomocí možnosti upravit a pokračovat můžete provést různé změny členů modulů, jako jsou vlastnosti, metody a pole, a to v režimu pozastavení. Některé změny se ale nepodporují. Zejména příkaz Upravit a pokračovat nepodporuje přidávání, odstraňování ani změnu typu nebo podpisu žádného člena.  
  
 Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Přidání nového člena, pokud v žádném aktivním příkazu nejsou žádné výskyty názvu.  
  
- Odebrání vlastnosti nebo metody.  
  
- Změna podpisu vlastnosti nebo metody.  
  
- Přidání, přejmenování, přesunutí nebo odstranění pole.  
  
- Úprava libovolné metody, která používá obecné typy.  
  
- Změna modifikátorů přístupu pro vlastnost nebo metodu, například pro změnu `Public` na `Private` .  
  
- Odstranění nebo změna typu existujícího pole.  
  
### <a name="nested-type-declaration-edits"></a><a name="BKMK_NestedTypeDeclarationEdits"></a> Úpravy deklarace vnořeného typu  
 Příkaz Upravit a pokračovat nepodporuje přesunutí vnořeného typu na jiný obor názvů nebo typ.  
  
### <a name="structure-declaration-edits"></a><a name="BKMK_StructureDeclarationEdits"></a> Úpravy deklarace struktury  
 Většina změn v deklaracích struktury není povolená v režimu **pozastavení** v době úprav a pokračování. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Přejmenování nebo odstranění existující struktury.  
  
- Implementace nového rozhraní nebo odebrání implementace rozhraní.  
  
- Změna modifikátoru přístupu pro strukturu.  
  
### <a name="structure-member-declaration-edits"></a><a name="BKMK_StructureMemberDeclarationEdits"></a> Úpravy deklarace členů struktury  
 Pomocí možnosti upravit a pokračovat můžete provést nejrůznější změny členů struktury (vlastnosti, metody a pole) v režimu přerušení. Některé změny však nejsou podporovány, zejména změny, které mají vliv na deklaraci členů struktury. Konkrétně upravit a pokračovat nepodporuje následující změny:  
  
- Odebrání vlastnosti nebo metody.  
  
- Přidání nebo odebrání pole.  
  
- Změna podpisu vlastnosti nebo metody.  
  
- Úprava libovolné metody, která používá obecné typy.  
  
- Změna toho, zda deklarace vlastnosti nebo metody implementuje rozhraní.  
  
- Změna modifikátorů přístupu vlastnosti nebo metody (například změna `Public` na **soukromou**).  
  
- Odebrání pole.  
  
- Změna typu pole.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití úprav v režimu pozastavení pomocí funkce upravit a pokračovat](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Upravit a pokračovat (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
