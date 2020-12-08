---
title: Struktury a sjednocení | Microsoft Docs
description: Tento článek obsahuje odkazy na referenční popisy struktur a sjednocení v sadě Visual Studio Debugging SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f477b46083b5abd5b8e93593cc728b660b58d9
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845762"
---
# <a name="structures-and-unions"></a>Struktury a sjednocení
Níže jsou uvedené struktury a sjednocení v sadě Visual Studio Debugging SDK.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Určuje ID procesu, což může být buď ID systému, nebo identifikátor GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Popisuje podmínky, za kterých se zarážka aktivuje.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Popisuje rozlišení zarážky chyby, včetně umístění, programu a vlákna.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Určuje typ struktury sloužící k popisu umístění zarážky.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Definuje součásti, které popisují umístění zarážky na adrese v kódu.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Popisuje umístění zarážky, která je svázána přímo s adresou v laděném programu.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Popisuje umístění zarážky na řádku ve zdrojovém souboru kódu.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Popisuje umístění posunu zarážky na funkci v kódu.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Slouží k nastavení zarážek kódu na základě řetězce, který uživatel může zadat z rozhraní IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Slouží k nastavení zarážek dat, které jsou založeny na řetězci, který uživatel může zadat z rozhraní IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Popisuje rozlišení zarážky v konkrétním umístění.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Popisuje počet a podmínky, po kterých bude zarážka aktivována po předchozím předání.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Obsahuje informace potřebné k implementaci zarážky.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Obsahuje informace potřebné k implementaci zarážky (stejné jako struktura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , ale zahrnují identifikátor GUID dodavatele, omezení a zarážka s trasováním informace).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Popisuje umístění zarážky kódu.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Popisuje výsledek vazby datové zarážky.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Popisuje informace o vázané zarážce buď pro zarážku kódu, nebo pro datovou zarážku.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Určuje strukturu umístění rozlišení zarážky.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Popisuje pole řetězců.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Určuje informace o typu pole pořízených z metadat.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Popisuje volání funkce nebo metody.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Popisuje počítač, na kterém je spuštěn ladicí program.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Popisuje seznam identifikátorů GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Popisuje kontext paměti nebo kontext kódu.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Popisuje adresu v laděném programu.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Představuje jeden z mnoha různých typů adres.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Identifikuje vlastní prohlížeč nebo Vizualizér typů.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Popisuje vlastnost ladění, která zase popisuje objekt hierarchického charakteru, který má název, typ a hodnotu.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Popisuje odkaz.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Popisuje zpětný překlad na integrované vývojové prostředí (IDE) k zobrazení.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Popisuje výjimku nebo chybu za běhu vyvolanou laděným programem.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Popisuje místní proměnnou, parametr nebo jiné pole.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Popisuje rámec zásobníku.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Popisuje pole jedinečných identifikátorů pro dostupné moduly ladění.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Slouží k nastavení informací JustMyCode pro modul.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Popisuje konkrétní počítač.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Popisuje prvek pole v rámci pole.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Popisuje adresu pole třídy nebo struktury.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Popisuje adresu místní proměnné v rámci oboru (obvykle funkce nebo metody).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Popisuje adresu metody třídy.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Popisuje parametr metody nebo funkce.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Popisuje návratovou hodnotu z metody nebo funkce.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Popisuje typ pole pořízený z metadat.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Popisuje konkrétní modul (DLL, EXE nebo Assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Popisuje informace o stavu hledaných cest hledání symbolů.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Popisuje nativní adresu.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Popisuje typ pole pořízený ze symbolu PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Popisuje stav zarážky, která je připravena k vytvoření vazby na umístění kódu.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Popisuje proces.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Popisuje seznam objektů [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , které reprezentují uzly programu.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Popisuje procesy běžící v počítači.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Popisuje umístění řádku a sloupce v daném textu.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Popisuje vlastnosti vlákna.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Popisuje typ pole.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Popisuje fyzickou adresu.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Popisuje adresu, která je relativní vzhledem k `this` ukazateli ( `Me` v Visual Basic).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h, SH. h nebo EE. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Referenční informace k rozhraním API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
