---
title: Nastavení ClickOnce a aplikace | Microsoft Docs
description: Přečtěte si, jak fungují soubory nastavení aplikace v aplikaci ClickOnce a jak ClickOnce migruje nastavení, když se uživatel upgraduje na další verzi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96491dc192b6578abd725d5d69b7c9093e92b20c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896387"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce a nastavení aplikace
Nastavení aplikace pro model Windows Forms usnadňuje vytváření, ukládání a údržbu uživatelských předvoleb aplikace a uživatele na klientovi. Následující dokument popisuje, jak soubory nastavení aplikace fungují v aplikaci ClickOnce a jak ClickOnce migruje nastavení, když uživatel upgraduje na další verzi.

 Níže uvedené informace platí pouze pro výchozího zprostředkovatele nastavení aplikace, <xref:System.Configuration.LocalFileSettingsProvider> třídy. Pokud zadáte vlastního poskytovatele, určí tento poskytovatel způsob, jakým ukládá svá data a jak upgradovat její nastavení mezi verzemi. Další informace o poskytovatelích nastavení aplikace najdete v tématu [Architektura nastavení aplikace](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>Soubory nastavení aplikace
 Nastavení aplikace používá dva soubory: *\<app>.exe.config* a *user.config*, kde *aplikace* je název vaší model Windows Forms aplikace. V klientovi se vytvoří *user.config* , když aplikace poprvé ukládá nastavení s rozsahem uživatele. *\<app>.exe.config* naproti tomu bude před nasazením existovat, pokud definujete výchozí hodnoty pro nastavení. Visual Studio bude tento soubor automaticky zahrnovat při použití příkazu **publikovat** . Pokud vytvoříte aplikaci ClickOnce pomocí *Mage.exe* nebo *MageUI.exe*, je nutné zajistit, aby byl tento soubor součástí dalších souborů aplikace při naplnění manifestu aplikace.

 V model Windows Forms aplikaci, která není nasazena pomocí technologie ClickOnce, je soubor *\<app>.exe.config* aplikace uložen v adresáři aplikace, zatímco *user.config* soubor je uložen ve složce **Documents and Settings** uživatele. V aplikaci ClickOnce *\<app>.exe.config* žije v adresáři aplikace v mezipaměti aplikace ClickOnce a *user.config* žije v adresáři dat ClickOnce pro danou aplikaci.

 Bez ohledu na to, jak aplikaci nasazujete, nastavení aplikace zajišťuje bezpečný přístup pro čtení *\<app>.exe.config* a bezpečný přístup pro čtení a zápis do *user.config*.

 V aplikaci ClickOnce je velikost konfiguračních souborů používaných nastavením aplikace omezená na velikost mezipaměti ClickOnce. Další informace najdete v tématu [Přehled mezipaměti ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Upgrady verze
 Stejně jako každá verze aplikace ClickOnce je izolovaná od všech ostatních verzí, nastavení aplikace pro aplikaci ClickOnce je izolované i v nastavení jiných verzí. Když uživatel upgraduje na novější verzi vaší aplikace, nastavení aplikace porovná nejnovější nastavení verze (s nejvyšším číslem) s nastaveními dodanými s aktualizovanou verzí a sloučí nastavení do nové sady souborů nastavení.

 Následující tabulka popisuje, jak nastavení aplikace určuje, která nastavení se mají kopírovat.

|Typ změny|Akce upgradu|
|--------------------|--------------------|
|Nastavení přidáno do *\<app>.exe.config*|Nové nastavení se sloučí do *\<app>.exe.config* aktuální verze.|
|Nastavení odebrané z *\<app>.exe.config*|Staré nastavení se odebere z *\<app>.exe.config* aktuální verze.|
|Nastavení se změnilo jako výchozí. místní nastavení je pořád nastavené na původní výchozí hodnotu v *user.config*|Toto nastavení se sloučí do *user.config* aktuální verze s novou výchozí hodnotou jako hodnota.|
|Nastavení se změnilo jako výchozí. nastavení nastavené na jiný než výchozí v *user.config*|Toto nastavení se sloučí do *user.config* aktuální verze, přičemž zůstane zachovaná jiná než výchozí hodnota.|

Pokud jste vytvořili svou vlastní obálkovou třídu nastavení aplikace a chcete přizpůsobit logiku aktualizace, můžete <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metodu přepsat.

## <a name="clickonce-and-roaming-settings"></a>Nastavení ClickOnce a roamingu
 ClickOnce nepracuje s nastaveními roamingu, což umožňuje, aby soubor nastavení následoval na počítačích v síti. Pokud potřebujete nastavení roamingu, budete muset buď implementovat poskytovatele nastavení aplikace, který bude ukládat nastavení přes síť, nebo vyvinout vlastní třídy nastavení pro ukládání nastavení na vzdáleném počítači. Další informace o zprostředkovatelích nastavení najdete v tématu [Architektura nastavení aplikace](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Viz také
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Přehled nastavení aplikace](/dotnet/framework/winforms/advanced/application-settings-overview)
- [Přehled mezipaměti ClickOnce](../deployment/clickonce-cache-overview.md)
- [Přístup k místním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)