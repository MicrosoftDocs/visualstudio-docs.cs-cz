---
title: Ukázka doplňku Excel pro programové testování uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6dc6b4385130c6341b5b3545c6c9f71dc67457f5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672199"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Ukázka doplňku Excel pro programové testování uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento ukázkový doplněk pro [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] je navržený speciálně pro podporu programových testů uživatelského rozhraní excelových listů, které se zaznamenávají a spouštějí v Visual Studio Enterprise. Doplněk je vytvořen pomocí Visual Studio Tools for Office.

 Další informace o tom, jak vytvořit doplněk pro Excel, najdete v tématu [Návod: vytvoření prvního doplňku VSTO pro Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) nebo vyhledání doplňku na webu MSDN pro excelový doplněk.

 I když doplněk aplikace Excel není primárním předmětem této dokumentace rozšíření programového testu UI pro Excel, může být užitečné několik komentářů.

 Důležité části tohoto doplňku:

- `ThisAddIn` Třída – spravuje kanál vzdálené komunikace .NET mezi `ExcelUICommunicator` a [ukázkovým rozšířením programového testu UI pro Excel](../test/sample-coded-ui-test-extension-for-excel.md).

- `ExcelCodedUIAddinHelper_TemporaryKey.pfx` – certifikát zabezpečení pro testování doplňku.

- `ExcelUICommunicator` třída – Tato třída implementuje rozhraní `IExcelUICommunication`.

## <a name="thisaddin-class"></a>ThisAddIn – třída
 Většina této třídy je ve skutečnosti generována pomocí Visual Studio Tools for Office v souboru `ThisAddIn.Designer.cs` při vytváření projektu doplňku aplikace Excel.

 Členy, které je nutné implementovat, jsou obslužné rutiny událostí: `ThisAddIn_Startup()` a `ThisAddIn_Shutdown()`. Jejich účelem je inicializovat nebo zavřít kanál vzdálené komunikace .NET, který je používán `ExcelUICommunicator`.

## <a name="excelcodeduiaddinhelper_temporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey. pfx
 Tento soubor obsahuje dočasný certifikát zabezpečení, který je generován Visual Studio Tools for Office a poskytuje oprávnění sestavení doplňku pro práci v procesu aplikace Excel pro testování doplňku a rozšíření. Tento certifikát byste měli odstranit a buď vytvořit nový na kartě **podepisování** v okně **vlastnosti** projektu, nebo připojit vlastní testovací certifikát.

## <a name="exceluicommunicator-class"></a>ExcelUICommunicator – třída
 Tato třída implementuje rozhraní `IExcelUITestCommunication` a získá požadované informace o uživatelském rozhraní z modelu objektu aplikace Excel. Další informace najdete v tématu [ukázka rozhraní Excel Communicator](../test/sample-excel-communicator-interface.md).

## <a name="see-also"></a>Viz také
 [Rozšiřování programových testů uživatelského rozhraní a záznamů akcí pro podporu Microsoft Excelu](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [: vytvoření prvního doplňku VSTO pro Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) [Office a vývoj pro SharePoint](https://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329)
