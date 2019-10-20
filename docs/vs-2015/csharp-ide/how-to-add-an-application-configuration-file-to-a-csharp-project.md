---
title: 'Postupy: Přidání konfiguračního souboru aplikace do C# projektu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667530"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Postupy: Přidání konfiguračního souboru aplikace do projektu C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přidáním konfiguračního souboru aplikace (soubor App. config) do C# projektu můžete přizpůsobit, jak modul CLR (Common Language Runtime) hledá a načte soubory sestavení. Další informace o konfiguračních souborech aplikace najdete v tématu [jak modul runtime vyhledává sestavení](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

> [!NOTE]
> Windows Store nepodporuje <xref:System.Configuration>. V důsledku toho aplikace pro Store neobsahují šablonu App. config.

 Při sestavování projektu vývojové prostředí automaticky zkopíruje soubor App. config, změní název souboru kopie tak, aby odpovídal vašemu spustitelnému souboru, a pak přesune kopii do adresáře bin.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Přidání konfiguračního souboru aplikace do projektu C#

1. Na panelu nabídek vyberte možnost **projekt**, **Přidat novou položku**.

     Zobrazí se dialogové okno **Přidat novou položku** .

2. Rozbalte položku **nainstalováno**, rozbalte položku **vizuální C# položky**a poté zvolte šablonu **konfigurační soubor aplikace** .

3. Do textového pole **název** zadejte název a pak klikněte na tlačítko **Přidat** .

     Do projektu se přidá soubor s názvem App. config.

## <a name="see-also"></a>Viz také
 Správa nastavení [Konfigurace schématu konfiguračního souboru](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) [aplikace (.NET)](../ide/managing-application-settings-dotnet.md) [Konfigurace aplikací](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) [Postupy: konfigurace aplikace pro cílení na verzi .NET Framework](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717) [pomocí vývojového prostředí sady Visual Studio C# pro](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)