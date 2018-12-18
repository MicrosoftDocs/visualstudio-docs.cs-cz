---
title: Idiasymbol – | Dokumentace Microsoftu
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
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bd52443d4150b371bbaa1865978db9a72c5c616
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734151"
---
# <a name="idiasymbol"></a>IDiaSymbol
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Popisuje vlastnosti instance symbolu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaSymbol : IUnknown  
```  
  
## <a name="methods-in-alphabetical-order"></a>Metody v abecedním pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDiaSymbol`.  
  
> [!NOTE]
>  Symboly vrátí smysluplná data pouze pro některé z těchto metod, v závislosti na typu symbol. Pokud metoda vrátí `S_OK`, pak tato metoda vrátila smysluplná data.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Načte všechny podřízené objekty daného symbolu.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Načte podřízené objekty daného symbolu. Tato metoda je rozšířenou verzi [idiasymbol::findchildren –](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Načte podřízené objekty daného symbolu, které jsou platné na zadané adrese.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Načte podřízené objekty daného symbolu, které jsou platné na zadaný relativní virtuální adrese (RVA).|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Načte podřízené objekty daného symbolu, které jsou platné v zadané virtuální adresy.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Načte výčet, který umožňuje klientovi iterovat přes všechny vložené rámce na dané adrese.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Načte výčet, který umožňuje klientovi iterovat přes všechny vložené rámce na zadaný relativní virtuální adrese (RVA).|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Načte výčet, který umožňuje klientovi iterovat přes všechny vložené rámce na zadanou virtuální adresu (VA).|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci informace čísla řádku všech funkcí, které jsou vloženy, přímo nebo nepřímo v tento symbol.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci informace o číslech řádků všech funkcí, které jsou vloženy, přímo nebo nepřímo v tento symbol v rámci zadaný rozsah adres.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci informace o číslech řádků všech funkcí, které jsou vloženy, přímo nebo nepřímo v tento symbol v rámci zadaného relativní virtuální adresu (RVA).|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci informace o číslech řádků všech funkcí, které jsou vloženy, přímo nebo nepřímo v tento symbol v rámci zadané virtuální adresy (VA).|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Odpovídající hodnota značky zadány, tato metoda vrátí výčet symboly, které jsou obsaženy v této funkci zástupné procedury na zadaný relativní virtuální adrese.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Vrátí počet značky akcelerátoru ukazatel ve funkci se zakázaným inzerováním C++ AMP.|  
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Vrátí všechny akcelerátoru hodnoty značky ukazatele, které odpovídají funkci jazyka C++ AMP akcelerátor zástupné procedury.|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Načte modifikátor přístupu členu třídy.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Načte posunu součástí address umístění.|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Načte část oddílu umístění adresu.|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Získá příznak označující, zda jiný symbol odkazuje na tuto adresu.|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Načte hodnotu stáří databáze programu.|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Načte identifikátor symbol index typu pole.|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Načte identifikátor typu pole index symbolu.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Získá číslo hlavní verze back-end.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Získá číslo podverze back-end.|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Získá číslo sestavení back-end.|  
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Načte posun základní data.|  
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Načte pozici základní data.|  
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Načte symbol, ze které je založená ukazatel.|  
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Načte ID symbol, ze které je založená ukazatel.|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Získá značku typu jednoduchého typu.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Načte pozici bit umístění.|  
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Načte integrované druh typu HLSL.|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Vrátí ukazatel konvence volání metody.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Získá odkaz na nadřazené třídu symbolu.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Načte identifikátor nadřazené třídu symbolu.|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Získá příznak označující, zda symbol odkazuje na adresu kódu.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Získá příznak označující, zda byla symbol vygenerovaný kompilátorem.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Načte název kompilátor používá k vytvoření [Kompilantu](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Získá příznak označující, zda uživatelský datový typ má konstruktor.|  
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Načte obsahující symbol tento symbol.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Získá příznak označující, zda je uživatelský datový typ konstanty.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Získá počet položek v seznamu nebo pole.|  
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Získá počet rozsahů adres platný přidružených místního symbolu.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Získá příznak označující, zda funkce, která používá vlastní konvence volání.|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Získá počet bajtů dat symbol výrobce OEM.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Načte proměnné klasifikace dat symbolu.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Získá příznak popisující funkce upravit a pokračovat zkompilovaný program nebo jednotky.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Získá příznak označující, zda funkce používá Pokud vratky.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Načte front-endu hlavní číslo verze.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Načte front-endu vedlejší číslo verze.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Získá počet front-endu sestavení.|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Získá příznak označující, zda veřejnými symboly odkazuje na funkci.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Načte identifikátor GUID symbolu.|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Získá příznak označující, zda funkce obsahuje volání `alloca`.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Získá příznak označující, zda uživatelský datový typ má všechny operátory přiřazení definované.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Získá příznak označující, zda uživatelský datový typ má definovaný operátorů přetypování.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Získá příznak označující, zda kompilantu obsahuje všechny informace o ladění.|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Získá příznak označující, zda má funkce obslužná rutina výjimky C++-style.|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Získá příznak označující, zda má funkce obslužné rutiny asynchronní výjimky.|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Získá příznak označující, zda má funkce vložené sestavení.|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Získá příznak označující, zda funkce obsahuje příkaz longjmp (součást zpracování výjimek jazyka C-style).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Získá příznak označující, zda modul obsahuje spravovaný kód.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Získá příznak označující, jestli má uživatelský datový typ vnořené definice typu.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Získá příznak označující, zda funkce nebo kompilantu má kontroly zabezpečení, kompilaci (prostřednictvím [/GS (Kontrola zabezpečení vyrovnávací paměti)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) přepínač kompilátoru).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Získá příznak označující, zda má funkci Win32 – vizuální styl strukturovaného zpracování výjimek.|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Získá příznak označující, zda obsahuje funkce setjmp příkazu.|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Získá příznak označující, zda je uživatelský datový typ nepřímé virtuální základní třídy.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Získá příznak označující, zda byl označen funkci s atributem inline.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Získá příznak označující, zda má funkce vrácení z přerušení instrukce.|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Získá příznak označující, zda je funkce virtuální funkce základní třídy.|  
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Získá příznak označující, zda symbol odpovídá skupině sdílené místní proměnné v kódu zkompilovaném pro akcelerátor AMP C++.|  
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Získá příznak označující, zda symbol odpovídá *definice rozsahu symbol* pro komponentu značky v kódu zkompilovaném pro akcelerátor AMP C++ proměnné ukazatele. Definice rozsahu symbol je umístění proměnnou rozsahu adres.|  
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Určuje, zda symbol odpovídá symbol funkce nejvyšší úrovně pro shader kompilován pro akcelerátor, který odpovídá `parallel_for_each` volání.|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Získá příznak označující, zda data je součástí agregace mnoho symbolů.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Získá příznak označující, zda soubor symbolů obsahuje typy C.|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Získá příznak označující, zda modul byl převeden z Common Intermediate Language (CIL) do nativního kódu.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Získá příznak označující, zda je zarovnán prvky uživatelsky definovaný datový typ konkrétní hranice.|  
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Určuje, zda tento symbol představuje data High Level Shader Language (HLSL).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Získá příznak označující, zda modul byl kompilován s [/hotpatch (vytvoření Image vyměnitelné za provozu)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) přepínač kompilátoru.|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Získá příznak označující, zda byl spravované kompilantu propojené s LTCG propojovacího programu.|  
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Určuje, zda matice hlavní řádek.|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Získá příznak označující, zda je spravovaná kompilantu .netmodule (obsahující jenom metadata).|  
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Určuje, zda `this` ukazatel odkazuje na datový člen s vícenásobnou dědičnost.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Získá příznak označující, zda má funkce [naked](http://msdn.microsoft.com/library/69723241-05e1-439b-868e-20a83a16ab6d) atribut.|  
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Určuje, zda je proměnná je vypuštěn.|  
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Určuje, zda `this` ukazatel je založena na hodnotu symbolu.|  
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Určuje, zda tento symbol je ukazatel na datový člen.|  
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Určuje, zda tento symbol je ukazatel na členskou funkci.|  
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Určuje, zda proměnná nese návratovou hodnotu.|  
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Určuje, zda modul je zkompilován s možností/SDL.|  
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Určuje, zda `this` ukazatel odkazuje na datový člen s jednoduchou dědičnost.|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Získá příznak označující, zda data byl rozdělen do agregace samostatné symbolů.|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Získá příznak označující, zda je statická funkce nebo převodní rutina vrstvy.|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Získá příznak označující, zda soukromé symboly byly odebrány ze souboru symbolů.|  
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Určuje, zda `this` ukazatel odkazuje na datový člen s virtuální dědičnost.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Získá jazyk zdroje.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Získá počet bajtů paměti, které používají objekt reprezentovaný tímto symbolem.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Získá odkaz na lexikální nadřazené symbolu.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Načte identifikátor lexikální nadřazené symbolu.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Načte název souboru souboru knihovny nebo objekt, ze kterého byl načten objekt.|  
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Vrátí délku objektu rozsah adres, ve kterém je platná místního symbolu.|  
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Vrátí část oddílu počáteční rozsah adres, ve kterém je platná místního symbolu.|  
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Vrátí posunutí část počáteční rozsah adres, ve kterém je platná místního symbolu.|  
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Vrátí začátek rozsahu adres, ve kterém je platná místního symbolu.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Načte typ umístění datového symbolu.|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Načte dolní mez pole dimenze až po FORTRAN.|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Načte identifikátor symbol dolní mez pole dimenze až po FORTRAN.|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Načte typ cíle procesoru.|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Získá příznak, která udává, zda symbol odkazuje na spravovaný kód.|  
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Načte druh místo paměti.|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Získá příznak označující, zda symbol odkazuje na kód Microsoft Intermediate Language (MSIL).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Načte název symbolu.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Získá příznak označující, zda uživatelský datový typ je vnořený.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Získá příznak označující, zda je funkce označena [noinline](http://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) atribut.|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Získá příznak označující, zda je funkce deklarovaná s [noreturn](http://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) atribut.|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Získá příznak označující, jestli žádné řazení zásobníku nedala provést jako součást kontrolou zásobníku vyrovnávací paměti.|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Získá příznak označující, zda se nedospělo funkce nebo popisek.|  
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Vrátí počet značky akcelerátoru ukazatel ve funkci se zakázaným inzerováním C++ AMP.|  
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Získá počet parametrů, které se použijí k původnímu typu.|  
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Získá počet indexů registru.|  
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Získá počet řádků v matici.|  
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Získá počet sloupců v matici.|  
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Načte název souboru objektů.|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Načte typ ukazatel objektu pro metodu třídy.|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Načte symbolu `oemId` hodnotu.|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Načte symbolu `oemSymbolId` hodnotu.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Načte posun umístění symbolu.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Získá příznak označující, zda funkce nebo popisek obsahuje optimalizovaný kód stejně jako informace o ladění.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Získá příznak označující, jestli má uživatelský datový typ přetížené operátory.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Získá příznak označující, zda uživatelský datový typ je zabalena.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Načte typ platformy, pro který byl zkompilován program nebo kompilace.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Získá příznak, který tento určující, zda je funkce čistě virtuální.|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Získá pořadí až po FORTRAN multidimenzionálního pole.|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Získá příznak označující, zda je typem ukazatele odkaz.|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Načte register označení umístění.|  
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Načte typ registru.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Načte relativní virtuální adresu (RVA) umístění.|  
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Určuje, zda `this` ukazatel je označený jako s omezeným přístupem.|  
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Načte slotu vzorkovače.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Získá příznak označující, zda uživatelský datový typ se zobrazí v neglobální lexikálním oboru.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Načte hodnotu tohoto symbolu podpis.|  
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Získá velikost člen uživatelem definovaného typu.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Číslo pozice v umístění načte.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Načte název souboru zdrojového souboru.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Načte zdrojový soubor a číslo řádku, která označuje, kde je definován zadaný uživatelem definovaného typu.|  
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Načte stride matici nebo strided pole.|  
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Načte typ sub.|  
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Načte ID typu. sub|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Načte název souboru, ze kterého byly načteny symboly.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Načte identifikátor jedinečný symbol.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Načte typ třídění symbol.|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Načte posunu část cíle.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Načte relativní virtuální adresu (RVA) cíle.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Načte adresu část cíle.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Načte virtuální adresy (VA) cíle.|  
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Načte pozici textury.|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Načte logickou `this` likvidátor pro metodu.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Načte převodní rutina typ funkce.|  
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Načte časové razítko základní spustitelného souboru.|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Načte token metadat spravované funkce nebo proměnné.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Získá odkaz na podpis funkce.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Načte identifikátor typu symbolu.|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Načte pole hodnot typu specifických pro kompilátor pro tento symbol.|  
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Načte pole hodnot typu specifických pro kompilátor identifikátor pro tento symbol.|  
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Načte uav slot.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Načte různé uživatelem definovaný typ (UDT).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Získá příznak označující, zda je uživatelský datový typ nezarovnaných.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Načte nedekorovaný název upravena, C++ nebo propojení, název.|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|Rozšíření `get_undecoratedName` metodu, která načte nedekorovaný název na základě hodnoty pole rozšíření.|  
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Načte ID typu původní (bez úprav).|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Načte horní mez až po FORTRAN dimenze pole.|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Načte identifikátor symbol horní mez až po FORTRAN dimenze pole.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Načte hodnotu konstanty.|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Získá příznak označující, zda je virtuální funkce.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Načte virtuální adresy (VA) umístění.|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Získá příznak označující, zda je uživatelský datový typ virtuální základní třídy.|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Načte index pro tabulku virtuální základní přemístění.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Načte posun v tabulce virtuální funkce virtuální funkce.|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Načte posun virtuální základní ukazatele.|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Načte typ ukazatele virtuální základní tabulky.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Načte rozhraní symbol typu virtuální tabulky pro typ definovaný uživatelem.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Načte identifikátor tvar virtuální tabulky symbolu.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Získá příznak označující, zda je uživatelský datový typ volatile.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní získáte voláním jedné z následujících metod:  
  
-   [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
-   [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
-   [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
-   [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje způsob zobrazení místní proměnné funkce na dané relativní virtuální adrese. Profil také ukazuje, jak symboly různých typů jsou vzájemně souvisí.  
  
> [!NOTE]
>  `CDiaBSTR` je třída, která zabalí `BSTR` a automaticky zpracovává uvolnění řetězec při vytváření instance dostane mimo rozsah.  
  
```cpp#  
void DumpLocalVars( DWORD rva, IDiaSession *pSession )  
{  
    CComPtr< IDiaSymbol > pBlock;  
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )  
    {  
        Fatal( "Failed to find symbols by RVA" );  
    }  
    CComPtr< IDiaSymbol > pscope;  
    for ( ; pBlock != NULL; )  
    {  
        CComPtr< IDiaEnumSymbols > pEnum;  
        // local data search  
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )  
        {  
            Fatal( "Local scope findChildren failed" );  
        }  
        CComPtr< IDiaSymbol > pSymbol;  
        DWORD tag;  
        DWORD celt;  
        while ( pEnum != NULL &&  
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1)  
        {  
            pSymbol->get_symTag( &tag );  
            if ( tag == SymTagData )  
            {  
                CDiaBSTR name;  
                DWORD    kind;  
                pSymbol->get_name( &name );  
                pSymbol->get_dataKind( &kind );  
                if ( name != NULL )  
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );  
            }  
            else if ( tag == SymTagAnnotation )  
            {  
                CComPtr< IDiaEnumSymbols > pValues;  
                // local data search  
                wprintf_s( L"\tAnnotation:\n" );  
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )  
                    Fatal( "Annotation findChildren failed" );  
                pSymbol = NULL;  
                while ( pValues != NULL &&  
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&  
                        celt == 1 )  
                {  
                    CComVariant value;  
                    if ( pSymbol->get_value( &value ) != S_OK )  
                        Fatal( "No value for annotation data." );  
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );  
                    pSymbol = NULL;  
                }  
            }  
            pSymbol = NULL;  
        }  
        pBlock->get_symTag( &tag );   
        if ( tag == SymTagFunction )    // stop when at function scope  
            break;  
        // move to lexical parent  
        CComPtr< IDiaSymbol > pParent;  
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )  
            && pParent != NULL ) {  
            pBlock = pParent;  
        }  
        else  
        {  
            Fatal( "Finding lexical parent failed." );  
        }  
    };  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 `Header:` dia2.h  
  
 Knihovna: diaguids.lib  
  
 Knihovny DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumsymbolsbyaddr –](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [Idiaenumsymbols –](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession –](../../debugger/debug-interface-access/idiasession.md)   
 [Hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Symboly a značky symbolů](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Kompilant](../../debugger/debug-interface-access/compiland.md)



