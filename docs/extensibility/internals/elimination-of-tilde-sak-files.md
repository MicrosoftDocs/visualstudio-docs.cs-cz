---
title: Eliminace souborů ~ SAK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708505"
---
# <a name="elimination-of-sak-files"></a>Eliminace souborů ~ SAK
V modulu plug-in správy zdrojového kódu rozhraní API 1,2 byly soubory *~ sak* nahrazeny příznaky schopností a novými funkcemi, které zjišťují, zda modul plug-in správy zdrojových kódů podporuje soubor *MSSCCPRJ* a sdílené rezervace.

## <a name="sak-files"></a>~ SAK soubory
Aplikace Visual Studio .NET 2003 vytvořila dočasné soubory s předponou *~ sak*. Tyto soubory se používají k určení, zda modul plug-in správy zdrojových kódů podporuje:

- Soubor *MSSCCPRJ. SCC* .

- Vícenásobné (sdílené) rezervace.

Pro moduly plug-in, které podporují rozšířené funkce poskytované v rozhraní API modulu plug-in správy zdrojových kódů 1,2, může rozhraní IDE detekovat tyto možnosti bez vytváření dočasných souborů pomocí nových funkcí, příznaků a funkcí, které jsou podrobně popsané v následujících oddílech.

## <a name="new-capability-flags"></a>Nové příznaky schopností
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nové funkce
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Pokud modul plug-in správy zdrojových kódů podporuje vícenásobné (sdílené) rezervace, deklaruje `SCC_CAP_MULTICHECKOUT` možnost a implementuje `SccIsMultiCheckOutEnabled` funkci. Tato funkce je volána vždy, když dojde k operaci registrace na jakémkoli projektu se spravovanými zdroji.

 Pokud modul plug-in správy zdrojových kódů podporuje vytvoření a použití souboru *MSSCCPRJ. SCC* , deklaruje `SCC_CAP_SCCFILE` schopnost a implementuje rozhraní [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Tato funkce se volá se seznamem souborů. Funkce vrátí `TRUE' or 'FALSE` pro každý soubor, aby označoval, zda má Visual Studio pro něj použít soubor *MSSCCPRJ. SCC* . Pokud se modul plug-in správy zdrojových kódů rozhodne nepodporovat tyto nové funkce a funkce, může k zakázání vytváření těchto souborů použít následující klíč registru:

 **[HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol] DoNotCreateTemporaryFilesInSourceControl**  =  *DWORD: 00000001*

> [!NOTE]
> Pokud je tento klíč registru nastaven na *hodnotu DWORD: 00000000*, je ekvivalentní klíč k neexistujícímu a Visual Studio se stále pokusí vytvořit dočasné soubory. Pokud je ale klíč registru nastavený na *DWORD: 00000001*, Visual Studio se nepokusí vytvořit dočasné soubory. Místo toho předpokládá, že modul plug-in správy zdrojových kódů nepodporuje soubor *MSSCCPRJ. SCC* a nepodporuje sdílené rezervace.

## <a name="see-also"></a>Viz také
- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu verze 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
