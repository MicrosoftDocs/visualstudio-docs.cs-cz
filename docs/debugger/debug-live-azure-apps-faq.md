---
title: Nejčastější dotazy k ladění snímků | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e0d8839daac2d470f4275257bfcfbc83fc7a62f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911397"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Nejčastější dotazy k ladění snímků v aplikaci Visual Studio

Tady je seznam otázek, které se můžou zobrazit při ladění živých aplikací Azure pomocí Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Jaké jsou náklady na výkon při pořízení snímku?

Když Snapshot Debugger zachytí snímek aplikace, rozvětvení zpracuje proces aplikace a pozastaví rozvětvenou kopii. Při ladění snímku budete ladit proti rozvětvené kopii procesu. Tento proces trvá jenom 10-20 milisekund, ale nekopíruje celou haldu aplikace. Místo toho zkopíruje pouze stránku tabulky a nastaví stránky pro kopírování při zápisu. Pokud se některé objekty vaší aplikace v haldě změní, jejich příslušné stránky se zkopírují. Tato Syrovátka má každý snímek za malý objem paměti (v pořadí stovek kilobajtů pro většinu aplikací).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Co se stane, když mám Azure App Service s horizontálním škálováním (více instancí mojí aplikace)?

Pokud máte více instancí aplikace, snímkovací body se aplikuje na každou jednu instanci. Pouze první snímkovací bod, který se má vysáhnout se zadanými podmínkami vytvoří snímek. Pokud máte více snímkovací body, pozdější snímky pocházejí ze stejné instance, která vytvořila první snímek. Protokolovacích bodů odeslané do okna výstup bude zobrazovat pouze zprávy z jedné instance, zatímco protokolovacích bodů odesílání do protokolů aplikací odesílá zprávy ze všech instancí.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Jak Snapshot Debugger načte symboly?

Snapshot Debugger vyžaduje, abyste měli odpovídající symboly pro vaši aplikaci buď místně, nebo nasazené do Azure App Service. (Vložené soubory PDB se v tuto chvíli nepodporují.) Snapshot Debugger automaticky stáhne symboly z vašeho Azure App Service. Počínaje verzí Visual Studio 2017 verze 15,2, nasazení pro Azure App Service také nasadí symboly vaší aplikace.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Funguje Snapshot Debugger v sestavách pro vydání mé aplikace?

Ano – Snapshot Debugger je určeno pro práci s buildy vydaných verzí. Při umístění snímkovací bod do funkce je funkce znovu zkompilována zpět do ladicí verze, takže je možné ji ladit. Zastavení Snapshot Debugger vrátí funkce do verze buildu pro vydání.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Může protokolovacích bodů způsobit vedlejší účinky v mé produkční aplikaci?

Ne – všechny zprávy protokolu, které přidáte do vaší aplikace, se vyhodnocují prakticky. Nemůžou v aplikaci způsobit žádné vedlejší účinky. Některé nativní vlastnosti ale nemusí být dostupné pomocí protokolovacích bodů.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Funguje Snapshot Debugger, pokud je můj server v zatížení?

Ano, ladění snímků může fungovat pro servery, které jsou v zatížení. Snapshot Debugger omezuje a nezachytí snímky v situacích, kdy je na serveru málo volné paměti.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Návody odinstalovat Snapshot Debugger?

Rozšíření Snapshot Debugger lokality můžete odinstalovat v App Service pomocí následujících kroků:

1. Vypněte svůj App Service buď pomocí Průzkumníka cloudu v aplikaci Visual Studio, nebo Azure Portal.
1. Přejděte na web Kudu vašeho App Service (to znamená yourappservice.** SCM**. azurewebsites.NET) a přejděte na **rozšíření webu**.
1. Kliknutím na X na rozšíření Snapshot Debugger webu ho odeberte.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Proč jsou porty otevřené během Snapshot Debugger relace?

Snapshot Debugger musí otevřít sadu portů, aby bylo možné ladit snímky provedené v Azure, jsou to stejné porty, které jsou vyžadovány pro vzdálené ladění. [Seznam portů můžete najít tady](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Návody zakázat rozšíření vzdáleného ladicího programu?

Pro App Services:
1. Zakažte rozšíření vzdáleného ladicího programu prostřednictvím Azure Portal pro vaši App Service.
2. Azure Portal > okno prostředků služby Application Service > *nastavení aplikace*
3. Přejděte do části *ladění* a klikněte na tlačítko *vypnout* pro *vzdálené ladění*.

Pro AKS:
1. Aktualizujte souboru Dockerfile tak, aby se odebraly oddíly odpovídající [Visual Studio Snapshot Debugger v imagích Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Znovu sestavte a nasaďte upravenou image Docker.

V případě virtuálních počítačů nebo virtuálních počítačů můžete odebrat rozšíření vzdáleného ladícího programu, certifikáty, trezory klíčů a příchozí fondy NAT následujícím způsobem:

1. Odebrat rozšíření vzdáleného ladicího programu

   Existuje několik způsobů, jak zakázat vzdálený ladicí program pro virtuální počítače a sady škálování virtuálních počítačů:

      - Zakázání vzdáleného ladicího programu přes Průzkumníka cloudu

         - Průzkumník cloudu > prostředku virtuálního počítače > zakázat ladění (Zakázání ladění pro sadu škálování virtuálního počítače v Průzkumníkovi cloudu neexistuje).

      - Zakázání vzdáleného ladicího programu pomocí skriptů a rutin PowerShellu

         Pro virtuální počítač:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Pro Virtual Machine Scale Sets:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Zakázání vzdáleného ladicího programu pomocí Azure Portal
         - Azure Portal > > rozšíření pro virtuální počítač nebo virtuální počítač sady VM Scale Sets
         - Odinstalace rozšíření Microsoft. VisualStudio. Azure. RemoteDebug. VSRemoteDebugger

         > [!NOTE]
         > Virtual Machine Scale Sets – portál nepovoluje odebírání DebuggerListener portů. Budete muset použít Azure PowerShell. Podrobnosti najdete níže.

2. Odebrání certifikátů a Azure webtrezoru

   Při instalaci rozšíření vzdáleného ladicího programu pro virtuální počítač nebo virtuální počítače se vytvoří certifikáty klienta i serveru, aby se ověřil klient VS s prostředky virtuálních počítačů Azure nebo virtuálních počítačů.

   - Certifikát klienta

      Tento certifikát je certifikát podepsaný svým držitelem, který je umístěný v certifikátu:/CurrentUser/my/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Jeden ze způsobů, jak tento certifikát z počítače odebrat, je přes PowerShell.

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Certifikát serveru
      - Odpovídající kryptografický otisk certifikátu serveru je nasazený jako tajný kód do trezoru klíčů Azure. VS se pokusí najít nebo vytvořit Trezor klíčů s předponou MSVSAZ * v oblasti odpovídající virtuálnímu počítači nebo prostředku Virtual Machine Scale Sets. Všechny prostředky virtuálních počítačů nebo Virtual Machine Scale Sets nasazené do této oblasti budou sdílet stejný Trezor klíčů.
      - Pokud chcete odstranit tajný kód kryptografického otisku certifikátu serveru, přejdete na Azure Portal a najděte úložiště klíčů MSVSAZ * ve stejné oblasti, která je hostitelem vašeho prostředku. Odstraní tajný klíč, který by měl být označený. `remotedebugcert<<ResourceName>>`
      - Budete taky muset z prostředku odstranit tajný klíč serveru přes PowerShell.

      Pro virtuální počítače:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Pro Virtual Machine Scale Sets:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Odebrat všechny DebuggerListener příchozí fondy NAT (jenom virtuální počítače s měřítkem)

   Vzdálený ladicí program zavádí DebuggerListener fondy překladu adres (NAT), které se používají pro nástroj pro vyrovnávání zatížení škálovací sady.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Návody zakázat Snapshot Debugger?

Pro App Service:
1. Zakažte Snapshot Debugger pomocí Azure Portal pro vaši App Service.
2. Azure Portal > okno prostředků služby Application Service > *nastavení aplikace*
3. V Azure Portal odstraňte následující nastavení aplikace a uložte provedené změny.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Všechny změny nastavení aplikace spustí restart aplikace. Další informace o nastavení aplikace najdete v tématu [Konfigurace aplikace App Service v Azure Portal](/azure/app-service/web-sites-configure).

Pro AKS:
1. Aktualizujte souboru Dockerfile tak, aby se odebraly oddíly odpovídající [Visual Studio Snapshot Debugger v imagích Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Znovu sestavte a nasaďte upravenou image Docker.

Pro virtuální počítače/sady škálování virtuálních počítačů:

K dispozici je několik způsobů, jak Snapshot Debugger zakázat:
- Průzkumník cloudu > prostředku virtuálního počítače/sady škálování virtuálního počítače > zakázat diagnostiku

- Azure Portal > v okně prostředků virtuálního počítače nebo virtuálního počítače > rozšíření > Odinstalace rozšíření Microsoft. Insights. VMDiagnosticsSettings

- Rutiny PowerShellu z [AZ PowerShell](/powershell/azure/overview)

   Virtuální počítač:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Sady škálování virtuálních počítačů:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [Ladění živých aplikací ASP.NET pomocí Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Ladění živých ASP.NET počítačů Azure Virtual Machines\Virtual pro škálování pomocí Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Ladění Live ASP.NET Azure Kubernetes pomocí Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Řešení potíží a známé problémy pro ladění snímků](../debugger/debug-live-azure-apps-troubleshooting.md)
