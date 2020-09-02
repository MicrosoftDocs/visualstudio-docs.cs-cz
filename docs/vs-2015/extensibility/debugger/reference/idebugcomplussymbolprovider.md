---
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b70701aa9c4b339749554601e2a565c17697c6a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186518"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Představuje poskytovatele symbolů COM+ s metodami, které jsou specifické pro spravovaný kód.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 I když neexistují žádné oddělení mezi rozhraními, které jsou užitečné pro vyhodnocení výrazu (EE) a ty, které jsou určeny pro použití ladicím modulem (DE), budou pravděpodobně tyto metody považovat pouze za vývojáře: AreSymbolsLoaded, GetAddressesInModuleFromPosition, getentrypoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols a UpdateSymbols.  
  
## <a name="methods"></a>Metody  
 Kromě metod v rozhraní [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) toto rozhraní implementuje následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Určuje, zda jsou pro daný modul načteny symboly ladění s identifikátorem domény aplikace.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Vytvoří typ ze zadaného primitivního typu.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mapuje umístění dokumentu v zadaném modulu na pole adres ladění.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Načte informace o typu zadaného pole za danou adresu ladění.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Načte název sestavení pro daný modul a doménu aplikace.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Načte třídy se zadaným atributem, který jsou implementovány v daném programovacím jazyce.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Načte třídy se zadaným atributem v daném modulu.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Načte vstupní bod aplikace.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Načte adresu ve funkci, která představuje daný posun řádku.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Načte rozložení místních proměnných pro sadu metod.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Vrátí název přidružený k zadanému tokenu za daný objekt metadat.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Načte symboly ladění s daným nadřazeným atributem pro zadaný modul.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Načte čtečku symbolů, kterou má používat nespravovaný kód.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Načte se na typ symbolu, který je dán adresou pro ladění.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Určuje, zda je odstraněna funkce na zadané adrese pro ladění.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Určuje, zda je funkce na zadané adrese pro ladění považována za zastaralou.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Určuje, zda je kód na zadané adrese ladicího programu skrytý.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Načte zadané symboly ladění v paměti.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Načte symboly ladění daného datového proudu.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Nahradí aktuální symboly ladění pomocí těch v zadaném datovém proudu.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Uvolní symboly ladění pro zadaný modul z paměti.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualizuje symboly ladění v paměti se zadanými datovými proudy.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
