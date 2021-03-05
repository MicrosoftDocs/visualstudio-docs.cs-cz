---
description: Popisuje jednu operaci zpětného překladu pro integrované vývojové prostředí (IDE), které se má zobrazit.
title: DisassemblyData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b6053647d43563e7369793982c72683002ae0df5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170455"
---
# <a name="disassemblydata"></a>DisassemblyData
Popisuje jednu operaci zpětného překladu pro integrované vývojové prostředí (IDE), které se má zobrazit.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Členové
`dwFields`\
[DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Konstanta určující, která pole jsou vyplněna.

`bstrAddress`\
Adresa jako posun od určitého počátečního bodu (obvykle začátek přidružené funkce).

`bstrCodeBytes`\
Bajty kódu pro tuto instrukci.

`bstrOpcode`\
Operační kód pro tuto instrukci.

`bstrOperands`\
Operandy pro tuto instrukci.

`bstrSymbol`\
Název symbolu, který je přidružen k adrese (veřejný symbol, popisek atd.).

`uCodeLocationId`\
Identifikátor umístění kódu pro tento přeložený řádek Pokud je adresa kontextu kódu na jednom řádku větší než adresa kontextu kódu jiné, pak identifikátor přeloženého umístění kódu prvního bude také větší než identifikátor umístění kódu druhé.

`posBeg`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , který odpovídá pozici v dokumentu, kde začíná data zpětného překladu.

`posEnd`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , který odpovídá pozici v dokumentu, kde končí data zpětného překladu.

`bstrDocumentUrl`\
U textových dokumentů, které mohou být reprezentovány jako názvy souborů, `bstrDocumentUrl` je pole vyplněno názvem souboru, kde byl zdroj nalezen, ve formátu `file://file name` .

Pro textové dokumenty, které nemohou být reprezentovány jako názvy souborů, `bstrDocumentUrl` je jedinečný identifikátor pro dokument a ladicí stroj musí implementovat metodu [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) .

Toto pole může obsahovat také další informace o kontrolních součtech. Podrobnosti najdete v části poznámky.

`dwByteOffset`\
Počet bajtů, které instrukce pochází od začátku řádku kódu.

`dwFlags`\
[DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) konstanta, která určuje, které příznaky jsou aktivní.

## <a name="remarks"></a>Poznámky
Každá `DisassemblyData` Struktura popisuje jednu instrukci zpětného překladu. Pole těchto struktur je vráceno z metody [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) se používá jenom pro textové dokumenty. Rozsah zdrojového kódu pro tuto instrukci je vyplněný jenom pro první instrukci generovanou z příkazu nebo řádku, například když `dwByteOffset == 0` .

Pro dokumenty, které nejsou textové, lze z kódu získat kontext dokumentu a `bstrDocumentUrl` pole by mělo mít hodnotu null. Pokud `bstrDocumentUrl` je pole stejné jako `bstrDocumentUrl` pole v předchozím `DisassemblyData` prvku pole, pak nastavte na `bstrDocumentUrl` hodnotu null.

Pokud `dwFlags` má pole `DF_DOCUMENT_CHECKSUM` nastaven příznak, pak další informace kontrolního součtu následují za řetězcem, na který je odkazováno v `bstrDocumentUrl` poli. Konkrétně po konci řetězce s hodnotou null existuje identifikátor GUID, který identifikuje algoritmus kontrolního součtu, který je zase následován hodnotou 4 bajtu, která označuje počet bajtů v kontrolním součtu a následně následován bajty kontrolního součtu. Podívejte se na příklad v tomto tématu o tom, jak toto pole zakódovat a dekódovat v [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

## <a name="example"></a>Příklad
`bstrDocumentUrl`Pole může obsahovat další informace kromě řetězce, pokud `DF_DOCUMENT_CHECKSUM` je nastaven příznak. Proces vytvoření a čtení tohoto kódovaného řetězce je jednoduchý [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] . V nástroji [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] je však další záležitost. Pro ty, kteří jsou zajímá, následující příklad ukazuje jeden ze způsobů, jak vytvořit kódovaný řetězec z [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] a jeden způsob, jak dekódovat kódovaný řetězec v [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Oprávnění](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
