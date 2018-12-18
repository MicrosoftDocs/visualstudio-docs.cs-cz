---
title: 'Postupy: potlačení upozornění kompilátoru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7cb1bbc637b51ecf75c0b491a5918ceaa147aa8f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932309"
---
# <a name="how-to-suppress-compiler-warnings"></a>Postupy: Potlačení upozornění kompilátoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadáním jednoho nebo více druhů upozornění kompilátoru, že nechcete, aby mohla obsahovat můžete declutter protokolu sestavení. Například můžete použít tuto techniku ke kontrole některé, ale ne všechny informace, které se automaticky vygeneruje, když nastavíte úroveň podrobností protokolu sestavení na Normal, Detailed nebo diagnostiky. Další informace o podrobnosti najdete v tématu [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Chcete-li potlačit specifická upozornění pro Visual C# nebo F #  
  
1.  V **Průzkumníka řešení**, vyberte projekt, ve kterém chcete potlačit upozornění.  
  
2.  V panelu nabídky zvolte **zobrazení**, **stránky vlastností**.  
  
3.  Zvolte **sestavení** stránky.  
  
4.  V **potlačit upozornění** pole, zadejte chybových kódů upozornění, která chcete potlačit, oddělené středníky a poté znovu sestavte řešení.  
  
### <a name="to-suppress-specific-warnings-for-visual-c"></a>Chcete-li potlačit specifická upozornění jazyka Visual C++  
  
1.  V **Průzkumníka řešení**, vyberte projekt nebo zdrojového souboru, ve kterém chcete potlačit upozornění.  
  
2.  V panelu nabídky zvolte **zobrazení**, **stránky vlastností**.  
  
3.  Zvolte **vlastnosti konfigurace** kategorie, zvolte **C/C++** kategorie a klikněte na tlačítko **Upřesnit** stránky.  
  
4.  Proveďte jeden z následujících kroků:  
  
    -   V **zakázat specifická upozornění** zadejte chybových kódů upozornění, která chcete potlačit, oddělené středníky.  
  
    -   V **zakázat specifická upozornění** zvolte **upravit** a zobrazte další možnosti.  
  
5.  Zvolte **OK** tlačítko a pak znovu sestavte řešení.  
  
## <a name="suppressing-warnings-for-visual-basic"></a>Potlačení upozornění v jazyce Visual Basic  
 Upozornění kompilátoru specifické pro jazyk Visual Basic lze skrýt tak, že upravíte soubor .vbproj pro projekt. Můžete také použít [stránka kompilovat, Návrhář projektu](../ide/reference/compile-page-project-designer-visual-basic.md) potlačit upozornění podle kategorie. Další informace najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Chcete-li potlačit specifická upozornění v jazyce Visual Basic  
  
1. V **Průzkumníka řešení**, vyberte projekt, ve kterém chcete potlačit upozornění.  
  
2. V panelu nabídky zvolte **projektu**, **uvolnit projekt**.  
  
3. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **upravit**_ProjectName_**.vbproj**.  
  
    Soubor projektu je otevřený v editoru kódu.  
  
4. Vyhledejte `<NoWarn></NoWarn>` prvek v konfiguraci sestavení, které vytváříte.  
  
    Následující příklad ukazuje `<NoWarn></NoWarn>` element tučným písmem pro ladění konfiguraci buildu na x x86 platformy:  
  
   ```  
   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
       <PlatformTarget>x86</PlatformTarget>  
       <DebugSymbols>true</DebugSymbols>  
       <DebugType>full</DebugType>  
       <Optimize>false</Optimize>  
       <OutputPath>bin\Debug\</OutputPath>  
       <DefineDebug>true</DefineDebug>  
       <DefineTrace>true</DefineTrace>  
       <ErrorReport>prompt</ErrorReport>  
       <NoWarn></NoWarn>  
       <WarningLevel>1</WarningLevel>  
     </PropertyGroup>  
   ```  
  
5. Přidejte jedno nebo více čísel upozornění jako hodnotu `<NoWarn>` elementu. Pokud zadáte více čísel upozornění, oddělte je středníkem, jak ukazuje následující příklad.  
  
   ```  
   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
       <PlatformTarget>x86</PlatformTarget>  
       <DebugSymbols>true</DebugSymbols>  
       <DebugType>full</DebugType>  
       <Optimize>false</Optimize>  
       <OutputPath>bin\Debug\</OutputPath>  
       <DefineDebug>true</DefineDebug>  
       <DefineTrace>true</DefineTrace>  
       <ErrorReport>prompt</ErrorReport>  
       <NoWarn>40059,42024</NoWarn>  
       <WarningLevel>1</WarningLevel>  
     </PropertyGroup>  
   ```  
  
6. Uložte změny do souboru .vbproj.  
  
7. V panelu nabídky zvolte **projektu**, **znovu načíst projekt**.  
  
8. V panelu nabídky zvolte **sestavení**, **znovu sestavit řešení**.  
  
    **Výstup** okno přestane zobrazovat upozornění, která jste zadali.  
  
   Další informace najdete v tématu [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md)   
 [Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)



