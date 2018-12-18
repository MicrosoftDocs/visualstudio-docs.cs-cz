---
title: Struktury a sjednocení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab670d64f82f76170e83ff75a52d30a3bf4eae5e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755193"
---
# <a name="structures-and-unions"></a>Struktury a sjednocení
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Níže jsou struktury a sjednocení v aplikaci Visual Studio SDK ladění.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Určuje ID procesu, který může být ID systému nebo identifikátor GUID.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Popisuje podmínky, za kterých bude platit zarážku.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Popisuje řešení k chybě zarážku, včetně umístění, aplikace a vlákna.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Určuje typ struktury, na které se používají k popisu umístění zarážky.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Definuje součásti, které popisují umístění zarážky na adrese v kódu.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Popisuje umístění zarážky, který je vázán přímo na adresu v programu, který se právě ladí.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Popisuje umístění zarážky na řádku ve zdrojovém souboru kódu.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Popisuje umístění posunu zarážky na funkci v kódu.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Používá k nastavení kódu zarážky založené na řetězec, který může uživatel zadat z integrovaného vývojového prostředí.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Používá k nastavení datové zarážky, které jsou založeny na řetězec, který může uživatel zadat z integrovaného vývojového prostředí.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Popisuje řešení zarážky v konkrétním umístění.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Popisuje počet a podmínky, na kterých bude vyvoláno zarážku po s dřív Bezproblémová.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Obsahuje informace potřebné k implementaci zarážku.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Obsahuje informace potřebné k implementaci zarážky (stejné jako [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktura zahrnuje ale identifikátor GUID, omezení a zarážky s trasováním informace dodavatele).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Popisuje umístění zarážky kódu.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Popisuje výsledek vazby datové zarážky.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Popisuje informace o vázaná zarážka kódu zarážku nebo zarážku data.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Určuje strukturu řešení umístění zarážky.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Popisuje pole řetězců.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Určuje informace o typ pole z metadat.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Popisuje volání funkce nebo metody.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Popisuje počítače, na kterém je spuštěný ladicí program.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Popisuje seznamu identifikátorů GUID.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Popisuje místní paměti nebo kontext kódu.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Popisuje adresu v programu, který se právě ladí.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Představuje jeden z několika různých druhů adresy.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Určuje vlastní prohlížeč nebo zadejte vizualizér.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Popisuje vlastnost, která ladění pak popisuje objekt hierarchickou povahu, který má název, typ a hodnotu.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Popisuje odkaz.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Popisuje převod do strojového jazyka do integrovaného vývojového prostředí pro zobrazení.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Popisuje výjimku nebo chyb za běhu vyvolané laděnému programu.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Popisuje místní proměnná, parametr nebo jiné pole.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Popisuje rámec zásobníku.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Popisuje celou řadu jedinečné identifikátory pro dostupné ladicí stroj.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Slouží k nastavení JustMyCode informace pro modul.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Popisuje konkrétní počítač.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Popisuje, k elementu pole v rámci pole.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Popisuje adresy pole třídy nebo struktury.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Popisuje adresu místní proměnné v rámci oboru (obvykle funkce nebo metoda).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Popisuje adresu metody třídy.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Popisuje parametr metody nebo funkce.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Popisuje návratovou hodnotu z metody nebo funkce.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Popisuje typ pole z metadat.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Popisuje konkrétního modulu (knihovny DLL, EXE nebo sestavení).  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Popisuje informace o vyhledávací cesty symbolů, které byly prohledány stavu.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Popisuje nativní adresu.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Popisuje typ pole z symbolů ze souboru PDB.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Popisuje stav zarážky, která jsou připravená k vytvoření vazby na místa v kódu.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Popisuje proces.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Seznam popisuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objekty, které představují uzly programů.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Popisuje procesy spuštěné na počítači.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Popisuje umístění řádku a sloupci v zadaném textu.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Popisuje vlastnosti vlákno.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Popisuje typ pole.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Popisuje fyzickou adresu.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Popisuje adresu, která je vzhledem k `this` ukazatel (`Me` v jazyce Visual Basic).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h sh.h či ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke knihovně API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)

