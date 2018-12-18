---
title: 'Návod: Vytvoření služby starší verze jazyka | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d80b40aa1db779c233dea846b49dbbc66084015
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783880"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Návod: Vytvoření služby starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Použití tříd jazyka spravovaného balíčku framework (MPF) k implementaci služba jazyka v [!INCLUDE[csprcs](../../includes/csprcs-md.md)] je jednoduché. Je třeba VSPackage pro hostování jazyková služba, samotné služby jazyka a analyzátor pro daný jazyk.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Umístění pro šablony sady Visual Studio balíčku projektu  
 Šabloně projektu balíček Visual Studio najdete ve třech umístěních jinou šablonu v **nový projekt** dialogové okno:  
  
1.  V části rozšiřitelnosti Visual Basic. Je výchozí jazyk projektu jazyka Visual Basic.  
  
2.  V jazyce C# rozšiřitelnosti. Je výchozí jazyk projektu C#.  
  
3.  V části Další typy rozšíření projektu. Výchozí jazyk projektu je C++.  
  
### <a name="create-a-vspackage"></a>Vytvoření VSPackage  
  
1.  Vytvoření nového balíčku VSPackage pomocí šablony projektu balíček Visual Studio.  
  
     Pokud přidáváte do existujícího balíčku VSPackage služba jazyka, následující kroky přeskočte a přejděte přímo na postup "Vytvoření Language Service třída".  
  
2.  Zadejte název projektu MyLanguagePackage a klikněte na **OK**.  
  
     Můžete použít jakýkoli název, který chcete. Tyto postupy, pomocí zde podrobně předpokládají MyLanguagePackage jako název.  
  
3.  Vyberte [!INCLUDE[csprcs](../../includes/csprcs-md.md)] jako jazyk a možnost vygenerovat nový soubor klíče. Klikněte na tlačítko **Další**.  
  
4.  Zadejte příslušné informace společnosti a balíčku. Klikněte na tlačítko **Další**.  
  
5.  Vyberte **příkazu nabídky**. Klikněte na tlačítko **Další**.  
  
     Pokud není pro podporu fragmenty kódu, stačí kliknutím na tlačítko Dokončit a další krok ignorovat.  
  
6.  Zadejte **Vložit fragment** jako **příkazu název** a `cmdidInsertSnippet` pro **ID příkazu**. Klikněte na tlačítko **Dokončit**.  
  
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
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#1)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#1)]  
  
7.  Upravit `MyLanguageService` třídy odvozovat <xref:Microsoft.VisualStudio.Package.LanguageService> třídy:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#2)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#2)]  
  
8.  Umístěte kurzor na "LanguageService" a od **upravit**, **IntelliSense** nabídce vyberte možnost **implementace abstraktní třídy**. Tento postup přidá minimální potřebné metody k implementaci třídy služba jazyka.  
  
9. Implementovat abstraktní metody, jak je popsáno v [implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Registrace služby jazyka  
  
1.  Otevřete soubor MyLanguagePackagePackage.cs a přidejte následující `using` příkazy:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguagepackagepackage.cs#3)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguagepackagepackage.vb#3)]  
  
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
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#4)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#4)]  
  
4.  Upravte třídu odvodit z požadovanou třídu MPF.  
  
5.  Přidat třídu konstruktor, který má alespoň stejné parametry jako konstruktor základní třídy a předat parametry konstruktoru k konstruktor základní třídy.  
  
     Například konstruktor pro třídu odvozenou z <xref:Microsoft.VisualStudio.Package.Source> třídy může vypadat třeba takto:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#5)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#5)]  
  
6.  Z **upravit**, **IntelliSense** nabídce vyberte možnost **implementace abstraktní třídy** Pokud základní třída má všechny abstraktní metody, které je třeba implementovat.  
  
7.  V opačném případě pozici blikajícího kurzoru uvnitř třídy a zadejte metodu k přepsání.  
  
     Zadejte například `public override` zobrazíte seznam všech metod, které mohou být přepsána nastaveními v dané třídy.  
  
## <a name="see-also"></a>Viz také  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)

