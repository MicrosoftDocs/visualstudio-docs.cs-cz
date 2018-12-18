---
title: 'Návod: Vytvoření služby starší verze jazyka | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98f5da733866143212ee4386bdeb88b3d0a2340a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865619"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Návod: Vytvoření služby starší verze jazyka
Použití tříd jazyka spravovaného balíčku framework (MPF) k implementaci služba jazyka v [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] je jednoduché. Je třeba VSPackage pro hostování jazyková služba, samotné služby jazyka a analyzátor pro daný jazyk.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Umístění pro šablony sady Visual Studio balíčku projektu  
 Šabloně projektu balíček Visual Studio najdete ve třech umístěních jinou šablonu v **nový projekt** dialogové okno:  
  
1.  V části rozšiřitelnosti Visual Basic. Je výchozí jazyk projektu jazyka Visual Basic.  
  
2.  V jazyce C# rozšiřitelnosti. Je výchozí jazyk projektu C#.  
  
3.  V části Další typy rozšíření projektu. Výchozí jazyk projektu je C++.  
  
### <a name="create-a-vspackage"></a>Vytvoření VSPackage  
  
1. Vytvoření nového balíčku VSPackage pomocí šablony projektu balíček Visual Studio.  
  
    Pokud přidáváte do existujícího balíčku VSPackage služba jazyka, následující kroky přeskočte a přejděte přímo na postup "Vytvoření Language Service třída".  
  
2. Zadejte název projektu MyLanguagePackage a klikněte na **OK**.  
  
    Můžete použít jakýkoli název, který chcete. Tyto postupy, pomocí zde podrobně předpokládají MyLanguagePackage jako název.  
  
3. Vyberte [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jako jazyk a možnost vygenerovat nový soubor klíče. Klikněte na tlačítko **Další**.  
  
4. Zadejte příslušné informace společnosti a balíčku. Klikněte na tlačítko **Další**.  
  
5. Vyberte **příkazu nabídky**. Klikněte na tlačítko **Další**.  
  
    Pokud není pro podporu fragmenty kódu, stačí kliknutím na tlačítko Dokončit a další krok ignorovat.  
  
6. Zadejte **Vložit fragment** jako **příkazu název** a `cmdidInsertSnippet` pro **ID příkazu**. Klikněte na tlačítko **Dokončit**.  
  
    **Název příkazu** a **ID příkazu** může být cokoliv, co chcete, ty jsou jenom příklady.  
  
### <a name="create-the-language-service-class"></a>Vytvořte třídu služby jazyka  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt MyLanguagePackage, zvolte **přidat**, **odkaz**a klikněte na tlačítko **přidat nový odkaz** tlačítko.  
  
2.  V **přidat odkaz** dialogu **Microsoft.VisualStudio.Package.LanguageService** v **.NET** kartě a klikněte na tlačítko **OK**.  
  
     To je potřeba udělat jenom jednou pro projekt jazyka balíčku.  
  
3.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt VSPackage a vyberte **přidat**, **třídy**.  
  
4.  Ujistěte se, že **třídy** je vybrán v seznamu šablon.  
  
5.  Zadejte **MyLanguageService.cs** pro název souboru třídy a klikněte na tlačítko **přidat**.  
  
     Můžete použít jakýkoli název, který chcete. Tyto postupy, pomocí zde podrobně předpokládají `MyLanguageService` jako název.  
  
6.  V souboru MyLanguageService.cs, přidejte následující `using` příkazy.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Upravit `MyLanguageService` třídy odvozovat <xref:Microsoft.VisualStudio.Package.LanguageService> třídy:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Umístěte kurzor na "LanguageService" a od **upravit**, **IntelliSense** nabídce vyberte možnost **implementace abstraktní třídy**. Tento postup přidá minimální potřebné metody k implementaci třídy služba jazyka.  
  
9. Implementovat abstraktní metody, jak je popsáno v [implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Registrace služby jazyka  
  
1.  Otevřete soubor MyLanguagePackagePackage.cs a přidejte následující `using` příkazy:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Zaregistrovat vaše třída jazyka služby, jak je popsáno v [registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md). To zahrnuje ProvideXX atributy a části "Proffering jazyk službu". Pokud toto téma používá TestLanguageService MyLanguageService použijte.  
  
### <a name="the-parser-and-scanner"></a>Analyzátor a skener  
  
1.  Jak je popsáno v implementaci analyzátor a skener pro váš jazyk [starší verze jazyka analyzátor a skener služby](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Jak implementovat analyzátor a skener je zcela v kompetenci vám a je nad rámec tohoto tématu.  
  
## <a name="language-service-features"></a>Funkce Language Service  
 Jednotlivé funkce implementovat ve službě jazyka, je obvykle odvodit třídu z příslušné třídy služba jazyka MPF implementovat všechny abstraktní metody podle potřeby a přepište odpovídající metody. Jaké třídy můžete vytvořit a/nebo odvozovat je závisí na funkcích chcete podporovat. Tyto funkce jsou popsány podrobně v [funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md). Následující postup je obecný postup k odvození třídy z třídy MPF.  
  
#### <a name="deriving-from-an-mpf-class"></a>Odvozování z třídy MPF  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt VSPackage a vyberte **přidat**, **třídy**.  
  
2.  Ujistěte se, že **třídy** je vybrán v seznamu šablon.  
  
     Zadejte vhodný název pro soubor třídy a klikněte na tlačítko **přidat**.  
  
3.  V novém souboru třídy přidejte následující `using` příkazy.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Upravte třídu odvodit z požadovanou třídu MPF.  
  
5.  Přidat třídu konstruktor, který má alespoň stejné parametry jako konstruktor základní třídy a předat parametry konstruktoru k konstruktor základní třídy.  
  
     Například konstruktor pro třídu odvozenou z <xref:Microsoft.VisualStudio.Package.Source> třídy může vypadat třeba takto:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Z **upravit**, **IntelliSense** nabídce vyberte možnost **implementace abstraktní třídy** Pokud základní třída má všechny abstraktní metody, které je třeba implementovat.  
  
7.  V opačném případě pozici blikajícího kurzoru uvnitř třídy a zadejte metodu k přepsání.  
  
     Zadejte například `public override` zobrazíte seznam všech metod, které mohou být přepsána nastaveními v dané třídy.  
  
## <a name="see-also"></a>Viz také  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)