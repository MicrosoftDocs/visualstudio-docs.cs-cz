---
title: Struktury a sjednocení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33e3f5ebb4e871f98b027638f5aae47d853828a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133970"
---
# <a name="structures-and-unions"></a>Struktury a sjednocení
Následují struktury a sjednocení v sadě Visual Studio ladění SDK.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Určuje Identifikátor procesu, který může být buď ID systému, nebo identifikátor GUID.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Popisuje podmínky, za kterých se aktivují zarážky.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Popisuje řešení zarážek k chybě, včetně umístění, program a přístup z více vláken.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Určuje typ struktury používají k popisu umístění zarážku.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Definuje součásti, které popisují umístění zarážek na adresu v kódu.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Popisuje umístění zarážek, který je vázaný přímo na adresu v programu laděné.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Popisuje umístění zarážek na řádku v souboru zdrojového kódu.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Popisuje umístění posunu zarážka v funkce v kódu.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Používá k nastavení kódu zarážky podle řetězec, který může uživatel zadat z prostředí IDE.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Používá k nastavení zarážek dat, které jsou založeny na řetězec, který může uživatel zadat z prostředí IDE.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Popisuje řešení zarážek na určité místo.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Popisuje, počet a podmínky, na kterých nebudou vydány boru přerušení po s byl dříve předán.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Obsahuje informace potřebné k implementaci zarážky.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Obsahuje informace potřebné k implementaci zarážku (stejné jako [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktura ale zahrnuje informace o identifikátor GUID, omezení a tracepoint dodavatele).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Popisuje umístění zarážek kódu.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Popisuje výsledek vazby dat zarážky.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Popisuje informace vázané breakpoint zarážku kódu nebo zarážku data.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Určuje strukturu zarážek umístění řešení.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Popisuje pole řetězců.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Určuje informace o typu pole prováděné z metadat.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Popisuje volání funkce nebo metoda.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Popisuje počítače, na kterém je spuštěný ladicího programu.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Popisuje seznamu identifikátorů GUID.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Popisuje kontextu paměti nebo kontext kódu.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Popisuje adresu v programu laděné.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Představuje jeden z několika různých druhů adresy.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Určuje vlastní prohlížeč nebo zadejte vizualizér.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Popisuje vlastnosti ladění, která pak dále popisuje objekt hierarchické povahy, který má název, typ a hodnotu.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Popisuje odkaz.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Popisuje zpětný překlad k prostředí IDE pro zobrazení.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Popisuje výjimku nebo Chyba při spuštění programu laděné vyvolané.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Popisuje, místní proměnné, parametr nebo jiné pole.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Popisuje rámce zásobníku.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Popisuje pole jedinečné identifikátory pro ladění k dispozici moduly.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Slouží k nastavení JustMyCode informace pro modul.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Popisuje konkrétní počítač.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Popisuje, k elementu pole v rámci pole.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Popisuje adresu pole třídu nebo strukturu.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Popisuje adresu místní proměnné v oboru (obvykle funkci nebo metodu).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Popisuje adresu metody třídy.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Popisuje parametr metody nebo funkce.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Popisuje vrácená hodnota z metody nebo funkce.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Popisuje typ pole prováděné z metadat.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Popisuje konkrétního modulu (knihovny DLL, EXE nebo sestavení).  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Popisuje informace o cesty pro hledání symbolu, které byly prohledány stavu.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Popisuje nativní adresy.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Popisuje typ pole převzat ze souboru PDB symbol.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Popisuje stav zarážek, který je připraven vytvořit vazbu na umístění kódu.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Popisuje proces.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Popisuje seznam [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objekty, které představují program uzly.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Popisuje procesy spuštěné na počítači.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Popisuje umístění, řádku a ve sloupci v zadaném textu.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Popisuje vlastnosti vlákno.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Popisuje typ pole.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Popisuje fyzickou adresu.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Popisuje adresu, která je vzhledem k `this` ukazatele (`Me` v jazyce Visual Basic).  
  
## <a name="requirements"></a>Požadavky  
 Hlavičky: msdbg.h, sh.h nebo ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke knihovně API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)