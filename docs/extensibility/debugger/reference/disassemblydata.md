---
title: DisassemblyData | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7ab7b278c03d092e1e559f1eb74f5d6bdc86d85
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816849"
---
# <a name="disassemblydata"></a>DisassemblyData
Popisuje jedna instrukce zpětný překlad pro integrované vývojové prostředí (IDE) pro zobrazení.  
  
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
 `dwFields`  
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) konstanta, která určuje, která pole jsou vyplněna.  
  
 `bstrAddress`  
 Adresa jako posun od některé počáteční bod (obvykle začátek přidružené funkce).  
  
 `bstrCodeBytes`  
 Počet bajtů kód pro tuto instrukci.  
  
 `bstrOpcode`  
 Operační kód pro tuto instrukci.  
  
 `bstrOperands`  
 Operandy pro tuto instrukci.  
  
 `bstrSymbol`  
 Název symbolu, pokud existuje, přidružené k adresám (veřejnými symboly, popisek a tak dále).  
  
 `uCodeLocationId`  
 Identifikátor umístění kódu pro tento řádek zpětně přeložený. Pokud adresu kontext kódu jeden řádek je větší než adresu kód kontextu, identifikátor umístění zpětně přeložený kód prvního také být větší než identifikátor umístění kódu druhého.  
  
 `posBeg`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , který odpovídá na pozici v dokumentu, kde začíná data zpětný překlad.  
  
 `posEnd`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , který odpovídá pozici v dokumentu, kde končí data zpětný překlad.  
  
 `bstrDocumentUrl`  
 Pro textové dokumenty, které můžou být vyjádřeny jako názvy souborů `bstrDocumentUrl` pole se vyplní název souboru, kde lze nalézt zdroj, pomocí formátu `file://file name`.  
  
 Pro textové dokumenty, které nemůže být reprezentovaná jako názvy souborů `bstrDocumentUrl` je jedinečný identifikátor pro dokument a ladicí stroj musí implementovat [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) metody.  
  
 Toto pole může obsahovat také další informace o kontrolních součtů. Podrobnosti najdete v části poznámky.  
  
 `dwByteOffset`  
 Počet bajtů, které se podle pokynů od začátku řádku kódu.  
  
 `dwFlags`  
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) konstanta, která určuje, které příznaky jsou aktivní.  
  
## <a name="remarks"></a>Poznámky  
 Každý `DisassemblyData` struktura popisuje jedna instrukce zpětný překlad. Vrátí pole těchto struktur [čtení](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metoda.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura se používá pro textový pouze dokumenty. Zdrojový kód rozsah pro tuto instrukci vyplnění jenom pro první instrukci nevygeneruje příkaz nebo řádku, například když `dwByteOffset == 0`.  
  
 Kód, můžete získat pro dokumenty, které jsou mimo textovou, kontext dokumentu a `bstrDocumentUrl` pole musí mít hodnotu null. Pokud `bstrDocumentUrl` pole je stejné jako `bstrDocumentUrl` pole v předchozí `DisassemblyData` prvek pole a pak nastavit `bstrDocumentUrl` na hodnotu null.  
  
 Pokud `dwFlags` pole má `DF_DOCUMENT_CHECKSUM` příznak nastaven, pak údaj o kontrolním součtu další následuje řetězec, který odkazuje `bstrDocumentUrl` pole. Konkrétně po řetězec s hodnotou null zakončení, existuje následuje identifikátor GUID identifikující kontrolního součtu algoritmus, který je zase následovaný 4 bajty. hodnota označující počet bajtů v kontrolního součtu a, který pak následuje kontrolní součet bajtů. Podívejte se na příklad v tomto tématu o tom, jak kódování a dekódování toto pole v [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
## <a name="example"></a>Příklad  
 `bstrDocumentUrl` Pole může obsahovat další informace než řetězce, pokud `DF_DOCUMENT_CHECKSUM` je nastavený příznak. Proces vytváření a čtení tohoto řetězce s kódováním je jednoduché v [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]. Nicméně v [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)], je další věci. Pro ty, kteří jsou zajímá vás, následující příklad ukazuje jeden způsob, jak vytvořit řetězec zakódovaný z [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] a jeden ze způsobů, jak k dekódování kódovaný řetězec v [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
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
  
               // Parse string out.  String is assumed to be Unicode.  
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
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Pro čtení](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
