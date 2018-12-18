---
title: Nasazování komponent COM s ClickOnce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8f4412c067ffd43a14a62cc722cf60ca1a883d9f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820288"
---
# <a name="deploying-com-components-with-clickonce"></a>Nasazování komponent COM s ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nasazení komponent modelu COM, starší verze tradičně těžký úkol. Součásti musí být globálně zaregistrovaní a proto může způsobit nežádoucí vedlejší účinky mezi aplikacemi se překrývají. Tato situace není obecně problém v aplikacích .NET Framework protože komponenty jsou naprosto izolované k aplikaci nebo jsou kompatibilní se vedle sebe. Visual Studio umožňuje nasadit izolované komponenty modelu COM na Windows XP nebo novější operační systém.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] poskytuje snadné a bezpečné mechanismus pro nasazení aplikací .NET. Nicméně pokud vaše aplikace používá starší verzi komponenty modelu COM, je potřeba provést další kroky pro jejich nasazení. Toto téma popisuje, jak nasadit izolované součásti COM a odkazovat na nativní součásti (například z jazyka Visual Basic 6.0 nebo Visual C++).  
  
 Další informace o nasazení izolované komponenty modelu COM, najdete v části "zjednodušení nasazení aplikací s [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a modelu COM bez registrace" v [ http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx ](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## <a name="registration-free-com"></a>COM bez registrace  
 COM bez registrace je nová technologie pro nasazení a aktivace izolované komponenty modelu COM. Funguje tak, že vložíte všechny komponenty knihovny typů a registrační informace, které je obvykle nainstalován do systémového registru do souboru XML s názvem manifestu, uloženy ve stejné složce jako aplikace.  
  
 Izolace komponenty modelu COM vyžaduje, aby byla registrována v počítači vývojáře, ale nemusí být registrován v počítači koncového uživatele. Izolovat komponenty modelu COM, je potřeba nastavit svůj odkaz **izolované** vlastnost **True**. Ve výchozím nastavení, tato vlastnost nastavena na **False**, která udává, že by měly být považovány za registrovaný odkaz modelu COM. Pokud je tato vlastnost **True**, způsobí, že manifest, který chcete pro tuto součást generována v okamžiku sestavení. Navíc způsobí, že odpovídající soubory, které se mají zkopírovat do složky aplikace během instalace.  
  
 Pokud generátor manifestu narazí izolované odkaz modelu COM, vypíše všechny `CoClass` položky v knihovně typů komponenty, odpovídající každé položce s jeho odpovídající registrační data a generování manifestu definice pro všechny modelu COM třídy v souboru knihovny typů.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Nasazování komponent COM bez registrace pomocí technologie ClickOnce  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologie nasazení je velmi vhodná pro nasazení izolované komponenty modelu COM, protože obě [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a modelu COM bez registrace nutné, aby komponenta manifestu pro nasazení.  
  
 Autor součásti obvykle by měla poskytnout manifestu. Pokud ne, Visual Studio je však podporuje generování manifestu pro komponenty modelu COM automaticky. Generování manifestu se provádí během [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] procesu publikování; Další informace najdete v tématu [publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md). Tato funkce také umožňuje využívat starší verze komponent, které jsou vytvořeny v dřívějších vývojových prostředích, jako je například Visual Basic 6.0.  
  
 Existují dva způsoby, které [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasadí komponenty modelu COM:  
  
-   Můžete nasadit komponenty modelu COM; zaváděcí nástroj Tento postup funguje na všech podporovaných platformách.  
  
-   Použijte nativní součásti nasazení izolace (označované také jako COM bez registrace). Ale bude to fungovat jenom na Windows XP nebo novější operační systém.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Příklad izolace a nasazení jednoduché komponenty modelu COM  
 Pro ukázání nasazení součásti COM bez registrace, v tomto příkladu se vytvoření aplikace pro Windows v jazyce Visual Basic, která odkazuje na izolované nativní součást COM vytvořené pomocí jazyka Visual Basic 6.0 a nasaďte ji pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 Nejprve musíte vytvořit nativní komponenty modelu COM:  
  
##### <a name="to-create-a-native-com-component"></a>Chcete-li vytvořit nativní komponenty modelu COM  
  
1.  Pomocí jazyka Visual Basic 6.0 **soubor** nabídky, klikněte na **nový**, pak **projektu**.  
  
2.  V **nový projekt** dialogové okno, vyberte **jazyka Visual Basic** uzel a vyberte možnost **ActiveX DLL** projektu. V **název** zadejte `VB6Hello`.  
  
    > [!NOTE]
    >  S modelem COM bez registrace, jsou podporovány pouze typy projektu ActiveX knihovny DLL a ovládacího prvku ActiveX ActiveX EXE a dokument ActiveX typy projektů nejsou podporovány.  
  
3.  V **Průzkumníka řešení**, dvakrát klikněte na panel **Class1.vb** otevřete textový editor.  
  
4.  V Class1.vb, přidejte následující kód za vygenerovaný kód `New` metody:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Začlenění komponenty. Z **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
> [!NOTE]
>  Bez registrace modelu COM podporuje pouze knihovny DLL a modelu COM Určuje typy projektů. Exe nelze použít s modelu COM bez registrace  
  
 Nyní můžete vytvořit aplikace pro systém Windows a přidejte odkaz na komponentu COM do ní.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Vytvoření aplikace založené na Windows pomocí komponenty modelu COM  
  
1. Pomocí jazyka Visual Basic z **souboru** nabídky, klikněte na tlačítko **nový**, pak **projektu**.  
  
2. V **nový projekt** dialogové okno, vyberte **jazyka Visual Basic** uzel a vyberte možnost **aplikace Windows**. V **název** zadejte `RegFreeComDemo`.  
  
3. V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko Zobrazit odkazy projektu.  
  
4. Klikněte pravým tlačítkem myši **odkazy** uzel a vyberte možnost **přidat odkaz** v místní nabídce.  
  
5. V **přidat odkaz** dialogové okno, klikněte na tlačítko **Procházet** kartu, přejděte na VB6Ahoj.dll a pak ho vyberte.  
  
    A **VB6Ahoj** odkazu se zobrazí v seznamu odkazů.  
  
6. Přejděte **nástrojů**, vyberte **tlačítko** ovládací prvek a přetáhněte ho na **Form1** formuláře.  
  
7. V **vlastnosti** tlačítka nastavte okně **Text** vlastnost **Hello**.  
  
8. Dvakrát klikněte na tlačítko Přidat kód obslužné rutiny a v souboru kódu přidejte kód tak, aby obslužná rutina načte následujícím způsobem:  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Spusťte aplikaci. Z **ladění** nabídky, klikněte na tlačítko **spustit ladění**.  
  
   Dále je třeba izolovat ovládacího prvku. Každé komponenty modelu COM, který používá vaše aplikace je v projektu reprezentována jako odkaz modelu COM. Tyto odkazy jsou zobrazeny v části **odkazy** uzlu **Průzkumníku řešení** okno. (Všimněte si, že přidáte odkazuje, buď přímo pomocí **přidat odkaz** příkaz **projektu** nabídky, nebo nepřímo přetažením ovládacího prvku ActiveX do formuláře.)  
  
   Následující kroky ukazují, jak izolovat komponenty modelu COM a publikování aktualizované aplikace obsahující izolované ovládacího prvku:  
  
##### <a name="to-isolate-a-com-component"></a>Chcete-li izolovat komponenty modelu COM  
  
1. V **Průzkumníka řešení**v **odkazy** uzlu, vyberte **VB6Ahoj** odkaz.  
  
2. V **vlastnosti** okno, změňte hodnotu **izolované** vlastnost z **False** k **True**.  
  
3. Z **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
   Teď, když stisknete klávesu F5, že aplikace funguje podle očekávání, ale je nyní spuštěna v rámci modelu COM bez registrace Aby bylo možné prokázat, zkuste součásti VB6Ahoj.dll a spustit RegFreeComDemo1.exe mimo rozhraní IDE sady Visual Studio. Tentokrát při klepnutí na tlačítko, stále funguje. Pokud přejmenujete dočasně manifestu aplikace, se znovu nezdaří.  
  
> [!NOTE]
>  Chybí komponenty modelu COM můžete simulovat dočasně zrušení registrace. Otevřete příkazový řádek, přejděte do složky systému tak, že zadáte `cd /d %windir%\system32`, poté zrušte registraci součásti tak, že zadáte `regsvr32 /u VB6Hello.dll`. Můžete ho zaregistrovat znovu tak, že zadáte `regsvr32 VB6Hello.dll`.  
  
 Posledním krokem je publikovat aplikace pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Chcete-li publikovat aktualizace aplikace s izolované komponenty modelu COM  
  
1. Z **sestavení** nabídky, klikněte na tlačítko **publikování RegFreeComDemo**.  
  
    Zobrazí se Průvodce publikováním.  
  
2. V Průvodci publikováním zadejte umístění na disku v místním počítači, kde lze získat přístup a zkontrolujte publikované soubory.  
  
3. Klikněte na tlačítko **Dokončit** publikování aplikace.  
  
   Když si zblízka publikované soubory, Všimněte si, že je soubor sysmon.ocx zahrnuté. Ovládací prvek je zcela izolován na tuto aplikaci, což znamená, že pokud má počítač koncového uživatele v jiné verzi ovládacího prvku jiná aplikace, ji nelze v konfliktu s touto aplikací.  
  
## <a name="referencing-native-assemblies"></a>Odkazování na nativní sestavení  
 Visual Studio podporuje odkazy na nativní jazyka Visual Basic 6.0 nebo sestavení C++; Tyto odkazy se nazývají nativní odkazy. Můžete zjistit, zda odkaz je nativní tak, že ověříte, že jeho **typ souboru** je nastavena na **nativní** nebo **ActiveX**.  
  
 Chcete-li přidat nativní referenci, použijte **přidat odkaz** příkaz a pak přejděte do manifestu. Některé součásti umístit manifest do knihovny DLL. V takovém případě můžete jednoduše zvolit samotná knihovna DLL a sady Visual Studio se ho přidat jako nativní odkaz zjistí, že součást obsahuje vloženého manifestu. Visual Studio také automaticky zahrne všechny závislé soubory nebo pokud jsou ve stejné složce jako odkazovaná součást uvedené v manifestu sestavení.  
  
 Izolování ovládacího prvku COM umožňuje snadno nasadit komponenty modelu COM, které ještě nemají manifesty. Nicméně pokud součást není zadána s manifestem, můžete odkazovat na manifest přímo. Ve skutečnosti by měla vždy použít manifest poskytnutý autorem komponenty, místo použití **izolované** vlastnost.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Omezení nasazení komponenty modelu COM bez registrace  
 COM bez registrace poskytuje jasné výhody oproti nasazení tradiční techniky. Existuje ale několik omezení a upozornění, které by měl být rovněž odkazován navýšení kapacity. Co největší omezení je, že funguje pouze na Windows XP nebo novějším. Implementace modelu COM bez registrace vyžaduje změny způsobu, ve kterém jsou načteny komponenty do jádra operačního systému. Bohužel neexistuje žádná podpora nižší úrovně vrstvy pro modelu COM bez registrace  
  
 Ne každá komponenta je vhodným kandidátem pro modelu COM bez registrace Součást není vhodný, pokud je splněna některá z následujících akcí:  
  
- Součást je out-of-process server. EXE servery nejsou podporovány. jsou podporovány pouze knihovny DLL.  
  
- Komponenta je součástí operačního systému, nebo je součástí systému, jako jsou XML, Internet Explorer nebo Microsoft Data Access Components (MDAC). Měli byste postupovat podle zásad automatické distribuce signatur autora součásti; Obraťte se na dodavatele.  
  
- Komponenta je součástí aplikace, jako je například Microsoft Office. Například by se neměly pokoušet izolovat objektový Model Microsoft Excel. To je součástí sady Office a jde použít jenom na počítači s plné verze produktu Office nainstalována.  
  
- Součást je určena pro použití jako doplněk nebo modul snap-in, například Office add-in nebo ovládací prvek ve webovém prohlížeči. Tyto součásti obvykle vyžadují nějaký druh schéma registrace určené hostitelské prostředí, který je mimo rozsah samotného manifestu.  
  
- Komponenta slouží ke správě fyzických nebo virtuálních zařízení pro systém, například ovladače zařízení pro zařazování tisku.  
  
- Součást je Data Access redistributable. Data aplikace obvykle vyžadují samostatné datové distribuovatelné součásti k instalaci, než budou moci spustit. By se neměly pokoušet izolovat komponenty, například ovládací prvek dat rozhraní ADO Microsoft, Microsoft OLE DB nebo Microsoft Data Access Components (MDAC). Místo toho pokud vaše aplikace používá MDAC nebo SQL Server Express, měli byste nastavit je jako požadavky; Zobrazit [postupy: instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  V některých případech může být možné vývojář komponenty přepracovat pro modelu COM bez registrace Pokud to není možné, můžete pořád vytvářet a publikovat aplikace, které jsou na nich závislé prostřednictvím schématu standardní registrace pomocí zaváděcí nástroj. Další informace najdete v tématu [vytváření balíčků Bootstrapperu](../deployment/creating-bootstrapper-packages.md).  
  
  Komponenty modelu COM může být pouze jednou izolovaný na aplikaci. Například nelze izolovat pod stejnou komponentou modelu COM ze dvou různých **knihovny tříd** projekty, které jsou součástí stejné aplikace. To způsobí upozornění sestavení a aplikace se nepodaří načíst v době běhu. Pokud se chcete vyhnout tomuto problému, společnost Microsoft doporučuje zapouzdřit komponenty modelu COM v jediné knihovny tříd.  
  
  Existuje několik scénářů, ve které modelu COM, je nutná registrace na počítači pro vývojáře, i když nasazení aplikace nepotřebuje registraci. `Isolated` Vlastnost vyžaduje zaregistrovat komponenty modelu COM na počítači pro vývojáře k automatické generování manifestu během sestavení. Neexistují žádné funkce zachytávání registrace, které vyvolají Automatická registrace během sestavování. Navíc všechny třídy, které nejsou explicitně definovány v knihovně typů se neprojeví v manifestu. Při použití komponenty modelu COM s již existující manifest, jako je například nativní referenci součást nemusí být registrováno v době vývoje. Registrace je však vyžaduje, pokud je součást ovládacího prvku ActiveX a chcete ho v **nástrojů** a Návrhář formulářů Windows.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)



