---
title: 'Postupy: Přidání konfiguračního souboru aplikace do projektu C# | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 43245704a2393b298f0f1d948d8a8829a4ef9bc4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204786"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Postupy: Přidání konfiguračního souboru aplikace do projektu C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přidejte konfigurační soubor aplikace (soubor app.config) do projektu C#, můžete přizpůsobit, jak modul common language runtime vyhledá a načte soubory sestavení. Další informace o konfiguračních souborech aplikace najdete v tématu [jak modul Runtime vyhledává sestavení](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
> [!NOTE]
>  Windows Store nepodporuje <xref:System.Configuration>. Aplikace pro Store v důsledku toho neobsahují šablonu souboru app.config.  
  
 Při sestavování projektu vývojové prostředí automaticky zkopíruje do souboru app.config, se změní název souboru kopie tak, aby odpovídaly spustitelný soubor a kopie je následně přesunuto do adresáře bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Přidání konfiguračního souboru aplikace do projektu C#  
  
1.  V panelu nabídky zvolte **projektu**, **přidat novou položku**.  
  
     **Přidat novou položku** zobrazí se dialogové okno.  
  
2.  Rozbalte **nainstalováno**, rozbalte **položky Visual C#** a klikněte na tlačítko **konfiguračního souboru aplikace** šablony.  
  
3.  V **název** textového pole zadejte název a klikněte na tlačítko **přidat** tlačítko.  
  
     Do projektu se přidá soubor s názvem souboru app.config.  
  
## <a name="see-also"></a>Viz také  
 [Správa nastavení aplikace (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Schéma konfiguračního souboru](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Konfigurace aplikací](http://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [Postupy: Konfigurace aplikace pro cílení na určitou verzi rozhraní .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Použití vývojového prostředí sady Visual Studio pro jazyk C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)