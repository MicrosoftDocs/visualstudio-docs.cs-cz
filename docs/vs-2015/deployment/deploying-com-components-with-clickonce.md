---
title: Nasazení komponent modelu COM pomocí technologie ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 6c83367881b7ed6a69fe10af8b7c68eb1692e3e6
ms.sourcegitcommit: 49ebf69986713e440fd138fb949f1c0f47223f23
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74706897"
---
# <a name="deploying-com-components-with-clickonce"></a>Nasazování komponent COM s ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nasazení starších komponent modelu COM bylo tradičně obtížné. Komponenty je potřeba globálně registrovat, takže můžou způsobit nežádoucí vedlejší účinky mezi překrývajícími se aplikacemi. Tato situace obvykle není problémem v aplikacích .NET Framework, protože komponenty jsou zcela izolované do aplikace nebo jsou souběžně kompatibilní. Visual Studio umožňuje nasadit izolované komponenty COM v operačním systému Windows XP nebo novějším.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] poskytuje snadný a bezpečný mechanismus pro nasazení aplikací .NET. Pokud však vaše aplikace používají starší komponenty modelu COM, budete muset provést další kroky pro jejich nasazení. Toto téma popisuje, jak nasadit izolované komponenty modelu COM a referenční nativní součásti (například z Visual Basic 6,0 nebo vizuálu C++).  
  
 Další informace o nasazení izolovaných komponent modelu COM naleznete v tématu [zjednodušení nasazení aplikace pomocí technologie ClickOnce a bez registrace com](/archive/msdn-magazine/2005/april/simplify-app-deployment-with-clickonce-and-registration-free-com).  
  
## <a name="registration-free-com"></a>COM bez registrace  
 COM bez registrace je nová technologie pro nasazení a aktivaci izolovaných komponent modelu COM. Funguje tak, že do souboru XML s názvem manifestu ukládá všechny informace o knihovně typů a registračních informací komponenty, které jsou obvykle nainstalovány do systémového registru, do souboru XML s názvem manifest uložený ve stejné složce jako aplikace.  
  
 Izolování komponenty modelu COM vyžaduje, aby byla zaregistrována v počítači vývojáře, ale nemusí být registrována v počítači koncového uživatele. K izolaci komponenty modelu COM, stačí, když nastavíte vlastnost **Isolated** na její odkaz na **hodnotu true**. Ve výchozím nastavení je tato vlastnost nastavena na **hodnotu false (NEPRAVDA**), která označuje, že by měla být považována za registrovaný odkaz com. Pokud má tato vlastnost **hodnotu true**, způsobí vygenerování manifestu pro tuto komponentu v čase sestavení. Také způsobí, že odpovídající soubory budou zkopírovány do složky aplikace během instalace.  
  
 Když generátor manifestu nalezne izolovaný odkaz modelu COM, vytvoří výčet všech položek `CoClass` v knihovně typů komponenty, porovnává každou položku s odpovídající registračními daty a generuje definice manifestu pro všechny třídy COM v souboru knihovny typů.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Nasazení komponent modelu COM bez registrace pomocí technologie ClickOnce  
 technologie nasazení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je vhodná pro nasazení izolovaných komponent modelu COM, protože [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a COM bez registrace vyžadují, aby komponenta měla manifest, aby se mohla nasadit.  
  
 Obvykle by autor komponenty měl poskytnout manifest. Pokud ne, Visual Studio však podporuje automatické generování manifestu pro komponentu COM. Generování manifestu se provádí během [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] procesu publikování; Další informace naleznete v tématu [publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md). Tato funkce také umožňuje využívat starší komponenty, které jste vytvořili ve starších vývojových prostředích, jako je Visual Basic 6,0.  
  
 Existují dva způsoby, jak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazují komponenty modelu COM:  
  
- Nasaďte komponenty COM pomocí zaváděcího nástroje. to funguje na všech podporovaných platformách.  
  
- Použijte nativní izolaci součástí (označuje se také jako nasazení COM bez registrace). Budou ale fungovat jenom v operačním systému Windows XP nebo novějším.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Příklad izolace a nasazení jednoduché komponenty COM  
 Aby bylo možné předvést nasazení komponenty modelu COM bez registrace, v tomto příkladu se v Visual Basic vytvoří aplikace pro systém Windows, která odkazuje na izolovanou nativní komponentu COM vytvořenou pomocí Visual Basic 6,0, a nasaďte ji pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 Nejprve budete muset vytvořit nativní součást COM:  
  
##### <a name="to-create-a-native-com-component"></a>Vytvoření nativní komponenty modelu COM  
  
1. Pomocí Visual Basic 6,0, v nabídce **soubor** klikněte na **Nový**a pak na **Project (projekt**).  
  
2. V dialogovém okně **Nový projekt** vyberte uzel **Visual Basic** a vyberte projekt **knihovny DLL ActiveX** . Do pole **název** zadejte `VB6Hello`.  
  
    > [!NOTE]
    > U modelu COM bez registrace je podporována pouze knihovna DLL ActiveX a typy projektů ovládacích prvků ActiveX; Typy projektu ActiveX a dokument ActiveX se nepodporují.  
  
3. V **Průzkumník řešení**dvakrát klikněte na **Class1. vb** a otevřete textový editor.  
  
4. V Class1. vb přidejte následující kód za generovaný kód pro metodu `New`:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5. Sestavte komponentu. V nabídce **sestavení** klikněte na **Sestavit řešení**.  
  
> [!NOTE]
> Model COM bez registrace podporuje pouze knihovny DLL a řízení typů projektu typu COM. Exe se nedá použít s COM bez registrace.  
  
 Nyní můžete vytvořit aplikaci založenou na systému Windows a přidat do ní odkaz na komponentu COM.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Vytvoření aplikace založené na systému Windows pomocí komponenty modelu COM  
  
1. Pomocí Visual Basic v nabídce **soubor** klikněte na **Nový**a pak na **Project (projekt**).  
  
2. V dialogovém okně **Nový projekt** vyberte uzel **Visual Basic** a vyberte možnost **aplikace systému Windows**. Do pole **název** zadejte `RegFreeComDemo`.  
  
3. V **Průzkumník řešení**kliknutím na tlačítko **Zobrazit všechny soubory** Zobrazte odkazy na projekt.  
  
4. Klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz** z místní nabídky.  
  
5. V dialogovém okně **Přidat odkaz** klikněte na kartu **Procházet** , přejděte na VB6Hello. dll a vyberte ji.  
  
    Odkaz na **VB6Hello** se zobrazí v seznamu odkazy.  
  
6. Najeďte na **panel nástrojů**, vyberte ovládací prvek **tlačítko** a přetáhněte ho do formuláře **Form1** .  
  
7. V okně **vlastnosti** nastavte vlastnost **text** tlačítka na hodnotu **Hello**.  
  
8. Dvojím kliknutím na tlačítko přidejte kód obslužné rutiny a do souboru kódu přidejte kód tak, aby obslužná rutina četla následující:  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Spusťte aplikaci. V nabídce **ladění** klikněte na **Spustit ladění**.  
  
   Dále je nutné izolovat ovládací prvek. Každá komponenta modelu COM, kterou vaše aplikace používá, je v projektu reprezentována jako odkaz COM. Tyto odkazy jsou viditelné pod uzlem **odkazy** v okně **Průzkumník řešení** . (Všimněte si, že můžete přidat odkazy buď přímo pomocí příkazu **Přidat odkaz** v nabídce **projekt** , nebo nepřímo přetažením ovládacího prvku ActiveX do formuláře.)  
  
   Následující kroky ukazují, jak izolovat komponentu modelu COM a publikovat aktualizovanou aplikaci obsahující izolovaný ovládací prvek:  
  
##### <a name="to-isolate-a-com-component"></a>Izolace komponenty modelu COM  
  
1. V **Průzkumník řešení**v uzlu **odkazy** vyberte odkaz **VB6Hello** .  
  
2. V okně **vlastnosti** změňte hodnotu vlastnosti **Isolated** z **false** na **true**.  
  
3. V nabídce **sestavení** klikněte na **Sestavit řešení**.  
  
   Když teď stisknete klávesu F5, aplikace funguje podle očekávání, ale teď je spuštěná v modelu COM bez registrace. Aby to bylo možné, zkuste zrušit registraci komponenty VB6Hello. dll a spustit RegFreeComDemo1. exe mimo prostředí Visual Studio IDE. Tentokrát funguje i po kliknutí na tlačítko. Pokud dočasně přejmenujete manifest aplikace, znovu se nezdaří.  
  
> [!NOTE]
> Nepřítomnost komponenty modelu COM můžete simulovat dočasným zrušením registrace. Otevřete příkazový řádek, do složky systému zadejte `cd /d %windir%\system32`a pak zrušte registraci komponenty zadáním `regsvr32 /u VB6Hello.dll`. Můžete ji znovu zaregistrovat zadáním `regsvr32 VB6Hello.dll`.  
  
 Posledním krokem je publikování aplikace pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Publikování aktualizace aplikace pomocí izolované komponenty modelu COM  
  
1. V nabídce **sestavení** klikněte na **publikovat RegFreeComDemo**.  
  
    Zobrazí se Průvodce publikováním.  
  
2. V průvodci publikování zadejte umístění na disku místního počítače, ke kterému máte přístup, a prověřte publikované soubory.  
  
3. Kliknutím na tlačítko **Dokončit** publikujte aplikaci.  
  
   Pokud prohlížíte publikované soubory, je třeba si uvědomit, že je zahrnutý soubor Sysmon. ocx. Ovládací prvek je zcela izolovaný k této aplikaci, což znamená, že pokud má počítač koncového uživatele jinou aplikaci, která používá jinou verzi ovládacího prvku, nemůže to kolidovat s touto aplikací.  
  
## <a name="referencing-native-assemblies"></a>Odkazování na nativní sestavení  
 Visual Studio podporuje odkazy na nativní Visual Basic 6,0 nebo C++ sestavení; Tyto odkazy se nazývají nativní odkazy. To, jestli je odkaz nativní, můžete zjistit tak, že ověříte, že jeho vlastnost **typu souboru** je nastavená na **nativní** , nebo na **ActiveX**.  
  
 Chcete-li přidat nativní odkaz, použijte příkaz **Přidat odkaz** a potom přejděte k manifestu. Některé součásti umístí manifest do knihovny DLL. V tomto případě můžete jednoduše zvolit samotnou knihovnu DLL a aplikace Visual Studio ji přidá jako nativní odkaz, pokud zjistí, že komponenta obsahuje vložený manifest. Visual Studio bude také automaticky zahrnovat všechny závislé soubory nebo sestavení, které jsou uvedeny v manifestu, pokud jsou ve stejné složce jako Odkazovaná komponenta.  
  
 Izolace řízení modelu COM usnadňuje nasazení komponent modelu COM, které ještě nemají manifesty. Nicméně pokud je komponenta dodávána s manifestem, můžete odkazovat přímo na manifest. Ve skutečnosti byste měli vždy použít manifest poskytnutý autorem součásti, kdykoli je to možné, a ne použít **izolovanou** vlastnost.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Omezení nasazení komponent modelu COM bez registrace  
 COM bez registrace poskytuje jasné výhody oproti tradičním technikám nasazení. Existuje však několik omezení a upozornění, která by také měla být navázána. Největší omezení je, že funguje jenom v systému Windows XP nebo novějším. Implementace modelu COM bez registrace vyžaduje změny způsobu, jakým jsou součásti načítány do základního operačního systému. Bohužel není k dispozici žádná vrstva podpory nižší úrovně pro model COM bez registrace.  
  
 Ne každá součást je vhodným kandidátem na registrační model COM bez registrace. Komponenta není vhodná, pokud platí některá z následujících podmínek:  
  
- Součást je mimo procesový Server. Servery EXE se nepodporují. podporovány jsou pouze knihovny DLL.  
  
- Součást je součástí operačního systému, nebo je součástí systému, jako je například XML, Internet Explorer nebo součásti MDAC (Microsoft Data Access Components). Měli byste postupovat podle zásad Redistribuce autora komponenty; obraťte se na dodavatele.  
  
- Součást je součástí aplikace, například systém Microsoft Office. Například byste se neměli pokoušet o izolaci objektového modelu Microsoft Excelu. Toto je součást Office a dá se použít jenom na počítači s nainstalovaným úplným produktem Office.  
  
- Součást je určena pro použití jako doplněk nebo modul snap-in, například doplněk pro Office nebo ovládací prvek ve webovém prohlížeči. Tyto komponenty obvykle vyžadují určitý druh registračního schématu definovaného hostujícím prostředím, který překračuje rozsah samotného manifestu.  
  
- Komponenta spravuje fyzické nebo virtuální zařízení pro systém, například ovladač zařízení pro službu zařazování tisku.  
  
- Komponenta je Distribuovatelný přístup k datům. Datové aplikace obecně vyžadují, aby byla před spuštěním nainstalována samostatná verze pro Distribuovatelný přístup k datům. Neměli byste se pokoušet izolovat komponenty, jako je například ovládací prvek dat Microsoft ADO, Microsoft OLE DB nebo součásti MDAC (Microsoft Data Access Components). Místo toho, pokud vaše aplikace používá MDAC nebo SQL Server Express, měli byste je nastavit jako požadavky. viz [Postup: instalace požadavků pomocí aplikace ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  V některých případech může být možné, aby vývojář součásti znovu navrhl návrh modelu COM bez registrace. Pokud to není možné, můžete i nadále sestavovat a publikovat aplikace, které jsou na nich závislé prostřednictvím standardního registračního schématu pomocí zaváděcího nástroje. Další informace najdete v tématu [vytváření balíčků zaváděcího nástroje](../deployment/creating-bootstrapper-packages.md).  
  
  Komponenta modelu COM může být pro každou aplikaci izolována pouze jednou. Například nemůžete izolovat stejnou komponentu modelu COM ze dvou různých projektů **knihoven tříd** , které jsou součástí stejné aplikace. V důsledku toho dojde k upozornění sestavení a aplikace se v době běhu nepodaří načíst. Chcete-li se tomuto problému vyhnout, společnost Microsoft doporučuje, abyste zapouzdřují komponenty modelu COM v jediné knihovně tříd.  
  
  Existuje několik scénářů, ve kterých se vyžaduje registrace modelu COM v počítači vývojáře, i když nasazení aplikace nevyžaduje registraci. Vlastnost `Isolated` vyžaduje, aby komponenta modelu COM byla registrována v počítači vývojáře, aby bylo možné automaticky generovat manifest během sestavení. Nejsou k dispozici žádné možnosti zachycení registrace, které během sestavení vyvolávají samočinnou registraci. Také se v manifestu neprojeví žádné třídy, které nejsou explicitně definovány v knihovně typů. Při použití komponenty modelu COM s již existujícím manifestem, jako je například nativní odkaz, nemusí být komponenta registrována v době vývoje. Registrace je však vyžadována, pokud je komponenta ovládacím prvkem ActiveX a chcete ji zahrnout do **sady nástrojů** a návrháře model Windows Forms.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)
