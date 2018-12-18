---
title: ClickOnce a nastavení aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d3cf6320401f58cd8ea1733e3b972202ba9b6d3
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081091"
---
# <a name="clickonce-and-application-settings"></a>Nastavení technologie ClickOnce a aplikace
Nastavení aplikace pro Windows Forms umožňuje snadno vytvářet, ukládat a udržovat vlastní aplikace a preference uživatelů v klientském počítači. Následující dokument popisuje, jak fungují soubory nastavení aplikace do aplikace ClickOnce, a jak ClickOnce migruje nastavení při upgradu na novou verzi.  
  
 Tyto informace se vztahují pouze k poskytovateli výchozí aplikaci nastavení \<xref:System.Configuration.LocalFileSettingsProvider > třída. Pokud zadáte vlastní poskytovatele, poskytovatel určí způsob, jakým ukládá svoje data a jak upgradu mezi verzemi jeho nastavení. Další informace o poskytovatelích nastavení aplikace najdete v tématu [architektura nastavení aplikace](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="application-settings-files"></a>Soubory nastavení aplikace  
 Nastavení aplikace využívá dva soubory:  *\<aplikace >. exe.config* a *user.config*, kde *aplikace* je název vaší aplikace Windows Forms. *User.config* se vytvoří na čas klienta první aplikace ukládá nastavení rozsahu uživatele. *\<Aplikace >. exe.config*, oproti tomu bude existovat před jejich nasazením při definování výchozí hodnoty pro nastavení. Visual Studio bude tento soubor obsahovat automaticky při použití jeho **publikovat** příkazu. Pokud vytvoříte aplikaci pomocí ClickOnce *Mage.exe* nebo *MageUI.exe*, je nutné tento soubor je součástí vaší aplikace na jiné soubory při naplňování manifest aplikace.  
  
 V aplikacích Windows Forms, není nasazená pomocí ClickOnce, aplikaci prvku  *\<aplikace >. exe.config* soubor je uložen v adresáři aplikace, zatímco *user.config* je uložený soubor v uživatele **Documents and Settings** složky. Do aplikace ClickOnce  *\<aplikace >. exe.config* se nachází v adresáři aplikace v mezipaměti aplikace ClickOnce a *user.config* umístěn v adresáři data ClickOnce pro tuto aplikaci.  
  
 Bez ohledu na to, jak nasadit aplikace, nastavení aplikace zajišťuje bezpečný přístup ke čtení  *\<aplikace >. exe.config*a bezpečné pro čtení a zápis přístup k *user.config*.  
  
 Do aplikace ClickOnce velikosti souboru konfigurace používají nastavení aplikace omezen velikostí mezipaměti technologie ClickOnce. Další informace najdete v tématu [ClickOnce – Přehled mezipaměti](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Upgrady verzí  
 Stejně jako každý verzi aplikace ClickOnce je izolovaný od ostatních verzí, jsou izolované od nastavení u jiných verzí i nastavení aplikace pro aplikaci ClickOnce. Když uživatel aktualizuje na novější verzi vaší aplikace, nastavení aplikace porovnává nejnovější (nejvyšší číslované) nastavení verze proti nastavení dodává s aktualizovanou verzi a sloučení nastavení na novou sadu souborů s nastavením.  
  
 Následující tabulka popisuje, jak určuje nastavení, které chcete kopírovat, nastavení aplikace.  
  
|Typ změny|Akce upgradu|  
|--------------------|--------------------|  
|Nastavení přidané do  *\<aplikace >. exe.config*|Nové nastavení je sloučen do aktuální verze  *\<aplikace >. exe.config*|  
|Odebrat z nastavení  *\<aplikace >. exe.config*|Původní nastavení se odebere z aktuální verze  *\<aplikace >. exe.config*|  
|Výchozí nastavení, které se změnily. místní nastavení stále nastavené na původní výchozí v *user.config*|Toto nastavení je sloučen do aktuální verze *user.config* nový výchozí hodnotu|  
|Výchozí nastavení, které se změnily. nastavení sady pro jiné než výchozí v *user.config*|Toto nastavení je sloučen do aktuální verze *user.config* s jinou než výchozí hodnotu uchovávají|  
  
Pokud jste vytvořili nastavení aplikace obálkovou třídu a chcete přizpůsobit logiku aktualizací, můžete přepsat \<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A > metoda.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce a nastavení roamingu  
 ClickOnce nefunguje s cestovní nastavení, která umožňuje soubor nastavení chcete postupovat podle různých počítačích v síti. Pokud potřebujete nastavení roamingu, musíte buď k implementaci poskytovatele nastavení aplikace, která ukládá nastavení v síti, nebo vyvíjet vlastní třídy vlastní nastavení pro ukládání nastavení ve vzdáleném počítači. Další informace v nastavení poskytovatelů najdete v tématu [architektura nastavení aplikace](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="see-also"></a>Viz také:  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Přehled nastavení aplikace](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [ClickOnce – Přehled mezipaměti](../deployment/clickonce-cache-overview.md)   
 [Přístup k lokálním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)