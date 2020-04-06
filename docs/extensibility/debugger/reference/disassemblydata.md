---
title: DemontážData | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737281"
---
# <a name="disassemblydata"></a>DisassemblyData
Popisuje jednu demontáž instrukce pro integrované vývojové prostředí (IDE) pro zobrazení.

## <a name="syntax"></a>Syntaxe

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
Konstanta [DISASSEMBLY_STREAM_FIELDS,](../../../extensibility/debugger/reference/disassembly-stream-fields.md) která určuje, která pole jsou vyplněna.

`bstrAddress`\
Adresa jako posun od některého počátečního bodu (obvykle začátek přidružené funkce).

`bstrCodeBytes`\
Kód bajtu pro tuto instrukci.

`bstrOpcode`\
Opcode pro tuto instrukci.

`bstrOperands`\
Operandy pro tuto instrukci.

`bstrSymbol`\
Případný název symbolu přidružený k adrese (veřejný symbol, popisek a tak dále).

`uCodeLocationId`\
Identifikátor umístění kódu pro tento rozložený řádek. Pokud je adresa kontextu kódu jednoho řádku větší než adresa kontextu kódu jiného, bude dezsestavený identifikátor umístění kódu prvního také větší než identifikátor umístění kódu druhého.

`posBeg`\
[TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) která odpovídá pozici v dokumentu, kde začíná data demontáže.

`posEnd`\
[TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) která odpovídá pozici v dokumentu, kde končí data demontáže.

`bstrDocumentUrl`\
U textových dokumentů, které mohou `bstrDocumentUrl` být reprezentovány jako názvy souborů, je pole vyplněno názvem souboru, kde lze zdroj nalézt, pomocí formátu `file://file name`.

Pro textové dokumenty, které nemohou `bstrDocumentUrl` být reprezentovány jako názvy souborů, je jedinečný identifikátor dokumentu a ladicí modul musí implementovat metodu [GetDocument.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

Toto pole může také obsahovat další informace o kontrolních součtech. Podrobnosti najdete v části Poznámky.

`dwByteOffset`\
Počet bajtů instrukce je od začátku řádku kódu.

`dwFlags`\
Konstanta [DISASSEMBLY_FLAGS,](../../../extensibility/debugger/reference/disassembly-flags.md) která určuje, které příznaky jsou aktivní.

## <a name="remarks"></a>Poznámky
Každá `DisassemblyData` struktura popisuje jednu instrukci demontáže. Pole těchto struktur je vrácena z [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody.

Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) se používá pouze pro textové dokumenty. Rozsah zdrojového kódu pro tuto instrukci je vyplněn pouze pro první instrukce `dwByteOffset == 0`generované z příkazu nebo řádku, například když .

Pro dokumenty, které nejsou textové, lze z kódu získat kontext `bstrDocumentUrl` dokumentu a pole by mělo mít nulovou hodnotu. Pokud `bstrDocumentUrl` je pole stejné `bstrDocumentUrl` jako pole `DisassemblyData` v předchozím prvku `bstrDocumentUrl` pole, nastavte hodnotu null.

Pokud `dwFlags` je v `DF_DOCUMENT_CHECKSUM` poli nastaven příznak, následují další informace kontrolního `bstrDocumentUrl` součtu za řetězcem, na který pole ukazuje. Konkrétně po zakončení nulového řetězce následuje identifikátor GUID identifikující algoritmus kontrolního součtu, který je zase následovaný hodnotou 4 bajtů označující počet bajtů v kontrolním součtu a za ním následují bajty kontrolního součtu. V tomto tématu najdete příklad kódování a dekódování tohoto pole v aplikaci [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].

## <a name="example"></a>Příklad
Pole `bstrDocumentUrl` může obsahovat další informace než `DF_DOCUMENT_CHECKSUM` řetězec, pokud je nastaven příznak. Proces vytváření a čtení tohoto kódovaného [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]řetězce je v . Nicméně, [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]v , to je jiná věc. Pro ty, kteří jsou zvědaví, následující příklad ukazuje jeden [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] způsob, jak vytvořit kódovaný řetězec [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]z a jeden způsob, jak dekódovat kódovaný řetězec v .

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
- [Čtení](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
