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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660491"
---
# <a name="sample-excel-communicator-interface"></a>Ukázka rozhraní komunikátoru Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ukázkové `IExcelUICommunication` rozhraní se používá v objektu `ExcelUICommunicator` v projektu `ExcelAddIn`.

## <a name="iexceluicommunication-interface"></a>Rozhraní IExcelUICommunication
 Toto rozhraní definuje komunikační body mezi `CodedUIExtension`, které běží v procesu programového testu uživatelského rozhraní, a `ExcelCodedUIAddIn`, která se spouští v procesu [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

 @No__t_0 sestavení má `ExcelUICommunicator` třídu, která je odvozena z tohoto rozhraní a používá objektový model aplikace Excel ke zpracování metod.

 Některé metody získají požadované informace z Excelu a pak vytvoří a vrátí jeden z informačních objektů, jako je `CellInformation` objekt.

 Jiné metody používají poskytnutý informační objekt, vyhledá odpovídající ovládací prvek v aplikaci Excel a na ovládacím prvku provede nějaký proces. Například metoda `ScrollIntoView` posune list tak, aby byla označená buňka viditelná.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>Komunikace CodedUIExtensibilitySample a ExcelCodedUIAddinHelper
 Sestavení `ExcelCodedUIAddinHelper` běží v procesu aplikace Excel a má `UICommunicator` třídu, která implementuje rozhraní `IExcelUITestCommunication` a získává nebo nastavuje požadované informace přímo z uživatelského rozhraní aplikace Excel.

 Sestavení `CodedUIExtensibilitySample` běží v procesu programového testu uživatelského rozhraní sady Visual Studio. Toto sestavení má třídu `Communicator`, která otevírá kanál vzdálené komunikace .NET a poskytuje vlastnost `Instance`, která používá rozhraní `IExcelUICommunication` k použití objektu `UICommunicator` v sestavení `ExcelCodedUIAddinHelper` k předávání požadavků a objektů informací. , jako je například objekt `CellInformation`, mezi dvěma sestaveními.

## <a name="see-also"></a>Viz také
 [Rozšiřování programových testů uživatelského rozhraní a záznamů akcí pro podporu](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [ukázkového doplňku](../test/sample-excel-add-in-for-coded-ui-testing.md) aplikace Microsoft Excel pro programový test UI ukázka programového [testu UI pro Excel](../test/sample-coded-ui-test-extension-for-excel.md)
