---
title: Symtagenum – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a9b3f28858bdeb6783175301de40de0d492739a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875214"
---
# <a name="symtagenum"></a>SymTagEnum
Určuje typ symbolu.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>Elementy  
 `SymTagNull`  
 Označuje, že symbol nemá žádný typ.  
  
 `SymTagExe`  
 Označuje, že symbol je soubor s příponou .exe. Existuje pouze jeden `SymTagExe` symbol za úložiště symbolů. Slouží jako globální obor a nemá žádné lexikální nadřazenou položku.  
  
 `SymTagCompiland`  
 Určuje symbol kompilace pro každou komponentu kompilantu úložišti symbolů. U nativních aplikací `SymTagCompiland` symboly odpovídají objektu soubory připojené do bitové kopie. Pro některé druhy Image Microsoft Intermediate Language (MSIL) je jedna kompilace na třídu.  
  
 `SymTagCompilandDetails`  
 Označuje, že symbol obsahuje rozšířené atributy souboru pro kompilaci. Načítání symbolů kompilace může vyžadovat načítání těchto vlastností.  
  
 `SymTagCompilandEnv`  
 Označuje, že symbol je řetězec prostředí definované pro souboru pro kompilaci.  
  
 `SymTagFunction`  
 Označuje, zda je symbol funkce.  
  
 `SymTagBlock`  
 Označuje, že symbol je vnořený blok.  
  
 `SymTagData`  
 Označuje, že je symbol data.  
  
 `SymTagAnnotation`  
 Označuje, že je pro komentování kódu symbol. Podřízené položky tohoto symbolu jsou řetězce konstantních dat (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Většina klientů Ignorovat tento symbol.  
  
 `SymTagLabel`  
 Označuje, že je symbol popisku.  
  
 `SymTagPublicSymbol`  
 Označuje, že symbol je veřejnými symboly. Pro nativní aplikace je tento symbol externích symbolů COFF došlo při propojování bitovou kopii k.  
  
 `SymTagUDT`  
 Označuje, že symbol je uživatelem definovaný typ (struktury, třídy nebo sjednocení).  
  
 `SymTagEnum`  
 Označuje, že symbol je výčet.  
  
 `SymTagFunctionType`  
 Určuje, zda je symbol typu podpis funkce.  
  
 `SymTagPointerType`  
 Označuje, že je symbol typu ukazatele.  
  
 `SymTagArrayType`  
 Určuje, zda je symbol typu pole.  
  
 `SymTagBaseType`  
 Označuje, že symbol základního typu.  
  
 `SymTagTypedef`  
 Určuje, zda je symbol `typedef`, to znamená, že alias pro jiného typu.  
  
 `SymTagBaseClass`  
 Označuje, že symbol je základní třídou uživatelem definovaného typu.  
  
 `SymTagFriend`  
 Označuje, že symbol je přátelská uživatelem definovaného typu.  
  
 `SymTagFunctionArgType`  
 Označuje, že symbol je jako argument funkce.  
  
 `SymTagFuncDebugStart`  
 Označuje, že je symbol koncového umístění kód prologu funkce.  
  
 `SymTagFuncDebugEnd`  
 Označuje, že symbol je počáteční umístění Kód epilogu funkce.  
  
 `SymTagUsingNamespace`  
 Označuje, že symbol je název oboru názvů, aktivní v aktuálním oboru.  
  
 `SymTagVTableShape`  
 Označuje, že symbol je popis virtuální tabulky.  
  
 `SymTagVTable`  
 Označuje, že symbol je ukazatel virtuální tabulky.  
  
 `SymTagCustom`  
 Označuje, že symbol je vlastní symbol a neinterpretuje sady  
  
 `SymTagThunk`  
 Označuje, že symbol je převodní rutina používá ke sdílení dat mezi 16 a 32 bitů kódu.  
  
 `SymTagCustomType`  
 Označuje, že symbol je vlastní kompilátoru symbol.  
  
 `SymTagManagedType`  
 Označuje, zda je symbol v metadatech.  
  
 `SymTagDimension`  
 Označuje, že symbol je až po FORTRAN vícerozměrné pole.  
  
 `SymTagCallSite`  
 Označuje, že symbol představuje lokalitu volání.  
  
 `SymTagInlineSite`  
 Označuje, že symbol představuje vložené lokality.  
  
 `SymTagBaseInterface`  
 Označuje, že symbol je základní rozhraní.  
  
 `SymTagVectorType`  
 Označuje, že je symbol typu vektoru.  
  
 `SymTagMatrixType`  
 Označuje, že je symbol typu matice.  
  
 `SymTagHLSLType`  
 Označuje, že je symbol typu vysokou úroveň Shader Language.  
  
## <a name="remarks"></a>Poznámky  
 Všechny symboly ladění souboru mají identifikační značky, který určuje typ symbolu.  
  
 Hodnoty v tomto výčtu jsou vráceny prostřednictvím volání [idiasymbol::get_symtag –](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metody.  
  
 Hodnoty v tento výčet se předají následující metody můžete omezit rozsah hledání, aby typ konkrétní symbolu:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: cvconst.h  
  
## <a name="see-also"></a>Viz také  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Idiasession::findsymbolbyaddr –](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [Idiasession::findsymbolbyrva –](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [Idiasession::findsymbolbyrvaex –](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [Idiasession::findsymbolbytoken –](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [Idiasession::findsymbolbyva –](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [Idiasession::findsymbolbyvaex –](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [Idiasession::findchildren –](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)