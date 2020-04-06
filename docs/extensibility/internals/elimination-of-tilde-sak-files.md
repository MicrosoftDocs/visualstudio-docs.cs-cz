---
title: Odstranění souborů ~SAK | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708505"
---
# <a name="elimination-of-sak-files"></a>Odstranění souborů ~SAK
V rozhraní API modulu plug-in správy zdrojového kódu 1.2 byly soubory *~SAK* nahrazeny příznaky schopností a novými funkcemi, které detekují, zda modul plug-in správy zdrojového kódu podporuje soubor *MSSCCPRJ* a sdílené pokladny.

## <a name="sak-files"></a>~Soubory SAK
Visual Studio .NET 2003 vytvořilo dočasné soubory s předponou *~SAK*. Tyto soubory se používají k určení, zda modul plug-in správy zdrojového kódu podporuje:

- Soubor *MSSCCPRJ.SCC.*

- Více (sdílených) výtek.

Pro moduly plug-in, které podporují pokročilé funkce poskytované v rozhraní API plug-in správy zdrojového kódu 1.2, ide můžete zjistit tyto možnosti bez vytváření dočasných souborů pomocí nových funkcí, příznaky a funkce, podrobně popsané v následujících částech.

## <a name="new-capability-flags"></a>Nové příznaky schopností
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nové funkce
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Pokud modul plug-in správy zdrojového kódu podporuje více (sdílených) povýběrů, deklaruje `SCC_CAP_MULTICHECKOUT` schopnost a implementuje `SccIsMultiCheckOutEnabled` funkci. Tato funkce je volána vždy, když dojde k operaci pokladny na některém z projektů řízených zdrojem.

 Pokud modul plug-in správy zdrojového kódu podporuje vytvoření a použití souboru *MSSCCPRJ.SCC,* pak deklaruje `SCC_CAP_SCCFILE` schopnost a implementuje Soubor [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Tato funkce je volána se seznamem souborů. Funkce vrátí `TRUE' or 'FALSE` pro každý soubor označující, zda Visual Studio by měl použít soubor *MSSCCPRJ.SCC* pro něj. Pokud se modul plug-in správy zdrojového kódu rozhodne nepodporovat tyto nové funkce a funkce, může zakázat vytváření těchto souborů pomocí následujícího klíče registru:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Pokud je tento klíč registru nastaven na *dword:00000000*, je ekvivalentní klíč je neexistující a Visual Studio stále pokouší vytvořit dočasné soubory. Pokud je však klíč registru nastaven na *dword:00000001*, aplikace Visual Studio se nepokusí vytvořit dočasné soubory. Místo toho předpokládá, že modul plug-in správy zdrojového kódu nepodporuje soubor *MSSCCPRJ.SCC* a nepodporuje sdílené pokladny.

## <a name="see-also"></a>Viz také
- [Co je nového v rozhraní Plug-in Plug-in API správy zdrojového kódu verze 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
