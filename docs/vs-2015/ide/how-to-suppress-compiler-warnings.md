---
title: 'Postupy: potlačení upozornění kompilátoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aeb404c479edec5dec89f28e80584d435f5c370a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670647"
---
# <a name="how-to-suppress-compiler-warnings"></a>Postupy: Potlačení upozornění kompilátoru

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Protokol sestavení můžete zaměnit zadáním jednoho nebo více druhů upozornění kompilátoru, které nechcete, aby obsahovaly. Můžete například použít tuto techniku ke kontrole některých, ale ne všech informací, které jsou generovány automaticky při nastavení podrobností protokolu sestavení na normální, podrobné nebo diagnostické. Další informace o podrobnostech najdete v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Chcete-li potlačit specifická C# upozornění pro Visual nebo F \#

1. V **Průzkumník řešení**vyberte projekt, ve kterém chcete potlačit upozornění.

2. Na panelu nabídek vyberte možnost **zobrazení**, **stránky vlastností**.

3. Vyberte stránku **sestavení** .

4. V poli **potlačit upozornění** určete chybové kódy upozornění, která chcete potlačit, oddělte je středníky a pak znovu sestavte řešení.

### <a name="to-suppress-specific-warnings-for-visual-c"></a>Chcete-li potlačit specifická upozornění pro vizuálC++

1. V **Průzkumník řešení**vyberte projekt nebo zdrojový soubor, ve kterém chcete potlačit upozornění.

2. Na panelu nabídek vyberte možnost **zobrazení**, **stránky vlastností**.

3. Zvolte kategorii **Vlastnosti konfigurace** , zvolte kategorii **CC++ /** kategorie a potom zvolte stránku **Upřesnit** .

4. Proveďte jeden z následujících kroků:

    - V poli **Zakázat specifická upozornění** určete chybové kódy upozornění, která chcete potlačit, a oddělte je středníkem.

    - V poli **Zakázat specifická upozornění** vyberte možnost **Upravit** a zobrazte další možnosti.

5. Klikněte na tlačítko **OK** a pak znovu sestavte řešení.

## <a name="suppressing-warnings-for-visual-basic"></a>Potlačení upozornění pro Visual Basic

Můžete skrýt specifická upozornění kompilátoru pro Visual Basic úpravou souboru. vbproj pro projekt. Můžete také použít [stránku kompilovat, Návrhář projektu](../ide/reference/compile-page-project-designer-visual-basic.md) pro potlačení upozornění podle kategorie. Další informace najdete v tématu [Konfigurace upozornění v Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Chcete-li potlačit specifická upozornění pro Visual Basic

1. V **Průzkumník řešení**vyberte projekt, ve kterém chcete potlačit upozornění.

2. V panelu nabídek vyberte položku **projekt**, **Uvolnit projekt**.

3. V **Průzkumník řešení**otevřete místní nabídku pro projekt a pak zvolte **Upravit**_ProjectName_ **. vbproj**.

    Soubor projektu je otevřen v editoru kódu.

4. Vyhledejte prvek `<NoWarn></NoWarn>` v konfiguraci sestavení, se kterou sestavíte.

    Následující příklad ukazuje prvek `<NoWarn></NoWarn>` v tučném textu pro konfiguraci sestavení ladění na platformě x86:

   ```xml
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

5. Přidejte jedno nebo více čísel upozornění jako hodnotu prvku `<NoWarn>`. Pokud zadáte více čísel upozornění, oddělte je čárkami, jak ukazuje následující příklad.

   ```xml
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

6. Uložte změny do souboru. vbproj.

7. V panelu nabídek vyberte položku **projekt**, **znovu načíst projekt**.

8. Na panelu nabídek vyberte **sestavení**, znovu **Sestavit řešení**.

    V okně **výstup** se již nezobrazuje upozornění, která jste zadali.

   Další informace najdete v tématu [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).

## <a name="see-also"></a>Viz také

- [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md)
- [Postupy: Zobrazování, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
