---
title: Rozhraní IWefDebuggingSupport –
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a4883d36c1833c66a2539380184521b070f5c2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544726"
---
# <a name="iwefdebuggingsupport-interface"></a>Rozhraní IWefDebuggingSupport –
  Implementováno ladicím prostředím, jako je například sada Visual Studio, pro usnadnění ladění aplikací pro Office. Aplikace Office, jako je Word nebo Excel, získá toto rozhraní ze sady Visual Studio a potom v rámci relace ladění zavolá metody v rozhraní v určitých okamžicích.

## <a name="syntax"></a>Syntax

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody, které definuje rozhraní IWefDebuggingSupport –.

|Název|Popis|
|----------|-----------------|
|[Metoda Getautoinsertextensions –](../vsto/getautoinsertextensions-method.md)|Načte informace o aplikacích pro Office, které se mají automaticky vkládat během ladění.|
|[Metoda Setwefprocessid –](../vsto/setwefprocessid-method.md)|Poskytuje identifikátor procesu, který spustí obsah architektury Web Extensions (WEF).|
