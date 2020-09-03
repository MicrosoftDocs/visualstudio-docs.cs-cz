---
title: Ukázka rozhraní Excel Communicator | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e3a9bd037c8886743910af649bf831b11337598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660491"
---
# <a name="sample-excel-communicator-interface"></a>Ukázka rozhraní komunikátoru Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ukázkové `IExcelUICommunication` rozhraní se používá v `ExcelUICommunicator` objektu v `ExcelAddIn` projektu.

## <a name="iexceluicommunication-interface"></a>Rozhraní IExcelUICommunication
 Toto rozhraní definuje komunikační body mezi `CodedUIExtension` , které běží v procesu programového testu uživatelského rozhraní, a `ExcelCodedUIAddIn` , který se spouští v [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] procesu.

 `ExcelCodedUIAddinHelper`Sestavení má `ExcelUICommunicator` třídu, která je odvozena z tohoto rozhraní a používá objektový model aplikace Excel ke zpracování metod.

 Některé metody získají požadované informace z Excelu a pak vytvoří a vrátí jeden z informačních objektů, jako je `CellInformation` objekt.

 Jiné metody používají poskytnutý informační objekt, vyhledá odpovídající ovládací prvek v aplikaci Excel a na ovládacím prvku provede nějaký proces. Například `ScrollIntoView` Metoda posune list tak, aby byla označená buňka viditelná.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>Komunikace CodedUIExtensibilitySample a ExcelCodedUIAddinHelper
 `ExcelCodedUIAddinHelper`Sestavení je spuštěno v aplikaci Excel a má `UICommunicator` třídu, která implementuje `IExcelUITestCommunication` rozhraní a získává nebo nastavuje požadované informace přímo z uživatelského rozhraní aplikace Excel.

 `CodedUIExtensibilitySample`Sestavení běží v procesu programového testu uživatelského rozhraní sady Visual Studio. Toto sestavení má `Communicator` třídu, která otevírá kanál vzdálené komunikace rozhraní .NET a poskytuje `Instance` vlastnost, která používá `IExcelUICommunication` rozhraní k použití `UICommunicator` objektu v `ExcelCodedUIAddinHelper` sestavení k předávání požadavků a objektů informací, jako je například `CellInformation` objekt, zpět a ze dvou sestavení.

## <a name="see-also"></a>Viz také
 [Rozšiřování programových testů uživatelského rozhraní a záznamů akcí pro podporu](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [ukázkového doplňku](../test/sample-excel-add-in-for-coded-ui-testing.md) aplikace Microsoft Excel pro programový test UI ukázka programového [testu UI pro Excel](../test/sample-coded-ui-test-extension-for-excel.md)
