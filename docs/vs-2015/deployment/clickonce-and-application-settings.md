---
title: Nastavení ClickOnce a aplikace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8e1ffe6d6f32cfad137d5890715a5a0032a29d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696692"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce a nastavení aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastavení aplikace pro model Windows Forms usnadňuje vytváření, ukládání a údržbu uživatelských předvoleb aplikace a uživatele na klientovi. Následující dokument popisuje, jak soubory nastavení aplikace fungují v aplikaci ClickOnce a jak ClickOnce migruje nastavení, když uživatel upgraduje na další verzi.  
  
 Níže uvedené informace platí pouze pro výchozího zprostředkovatele nastavení aplikace, <xref:System.Configuration.LocalFileSettingsProvider> třídy. Pokud zadáte vlastního poskytovatele, určí tento poskytovatel způsob, jakým ukládá svá data a jak upgradovat její nastavení mezi verzemi. Další informace o poskytovatelích nastavení aplikace najdete v tématu [Architektura nastavení aplikace](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>Soubory nastavení aplikace  
 Nastavení aplikace používá dva soubory: *aplikace*.exe.config a user.config, kde *aplikace* je název vaší model Windows Forms aplikace. V klientovi se vytvoří user.config, když aplikace poprvé ukládá nastavení s rozsahem uživatele. Pokud definujete výchozí hodnoty pro nastavení, bude mít *aplikace*.exe.config naproti tomu před nasazením. Visual Studio bude tento soubor automaticky zahrnovat při použití příkazu **publikovat** . Pokud vytvoříte aplikaci ClickOnce pomocí Mage.exe nebo MageUI.exe, je nutné zajistit, aby byl tento soubor součástí dalších souborů aplikace při naplnění manifestu aplikace.  
  
 V model Windows Formsch aplikacích, které nejsou nasazeny pomocí technologie ClickOnce, je soubor *aplikace.exe.config aplikace aplikace uložen* v adresáři aplikace, zatímco user.config soubor je uložen ve složce **Documents and Settings** uživatele. V *aplikaci ClickOnce aplikace.exe.config žije* v adresáři aplikace v mezipaměti aplikace clickonce a user.config žijí v adresáři dat ClickOnce pro danou aplikaci.  
  
 Bez ohledu na to, jak aplikaci nasazujete, nastavení aplikace zajišťuje bezpečný přístup pro čtení do *aplikace*.exe.config a bezpečný přístup pro čtení a zápis do user.config.  
  
 V aplikaci ClickOnce je velikost konfiguračních souborů používaných nastavením aplikace omezená na velikost mezipaměti ClickOnce. Další informace najdete v tématu [Přehled mezipaměti ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Upgrady verze  
 Stejně jako každá verze aplikace ClickOnce je izolovaná od všech ostatních verzí, nastavení aplikace pro aplikaci ClickOnce je izolované i v nastavení jiných verzí. Když uživatel upgraduje na novější verzi vaší aplikace, nastavení aplikace porovná nejnovější nastavení verze (s nejvyšším číslem) s nastaveními dodanými s aktualizovanou verzí a sloučí nastavení do nové sady souborů nastavení.  
  
 Následující tabulka popisuje, jak nastavení aplikace určuje, která nastavení se mají kopírovat.  
  
|Typ změny|Akce upgradu|  
|--------------------|--------------------|  
|Nastavení přidané do *aplikace*.exe.config|Nové nastavení se sloučí do *aplikace* aktuální verze.exe.config|  
|Nastavení odebrané z *aplikace*.exe.config|Staré nastavení se odebere z *aplikace* aktuální verze.exe.config|  
|Nastavení se změnilo jako výchozí. místní nastavení je pořád nastavené na původní výchozí hodnotu v user.config|Toto nastavení se sloučí do user.config aktuální verze s novou výchozí hodnotou jako hodnota.|  
|Nastavení se změnilo jako výchozí. nastavení nastavené na jiný než výchozí v user.config|Toto nastavení se sloučí do user.config aktuální verze, přičemž zůstane zachovaná jiná než výchozí hodnota.|  
  
 Pokud jste vytvořili svou vlastní obálkovou třídu nastavení aplikace a chcete přizpůsobit logiku aktualizace, můžete <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metodu přepsat.  
  
## <a name="clickonce-and-roaming-settings"></a>Nastavení ClickOnce a roamingu  
 ClickOnce nepracuje s nastaveními roamingu, což umožňuje, aby soubor nastavení následoval na počítačích v síti. Pokud potřebujete nastavení roamingu, budete muset buď implementovat poskytovatele nastavení aplikace, který bude ukládat nastavení přes síť, nebo vyvinout vlastní třídy nastavení pro ukládání nastavení na vzdáleném počítači. Další informace o zprostředkovatelích nastavení najdete v tématu [Architektura nastavení aplikace](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Přehled nastavení aplikace](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [Přehled mezipaměti ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Přístup k lokálním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
