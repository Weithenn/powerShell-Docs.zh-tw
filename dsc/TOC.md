# [概觀](overview.md)

## [適合決策者的預期狀態設定概觀](decisionMaker.md)

## [適合工程師的預期狀態設定概觀](DscForEngineers.md)

## [DSC 快速入門](quickStart.md)

# [設定](configurations.md)

## [制定組態](enactingConfigurations.md)

## [分離設定和環境資料](separatingEnvData.md)

## [使用多個版本的資源](sxsResource.md)

## [使用使用者認證執行 DSC](runAsUser.md)

## [指定節點之間的相依性](crossNodeDependencies.md)

## [設定資料](configData.md)

### [設定資料中的認證選項](configDataCredentials.md)

## [巢狀設定](compositeConfigs.md)

## [保護設定 MOF 檔案](secureMOF.md)

## [部分組態](partialConfigs.md)

## [撰寫 DSC 組態的說明](configHelp.md)

## [使用 DSC 在初始開機時設定虛擬機器](bootstrapDsc.md)

### [DSCAutomationHostEnabled 登錄機碼](DSCAutomationHostEnabled.md)

# [資源](resources.md)

## [內建資源](builtInResource.md)

### [封存資源](archiveResource.md)

### [環境資源](environmentResource.md)

### [檔案資源](fileResource.md)

### [群組資源](groupResource.md)

### [GroupSet 資源](groupSetResource.md)

### [記錄檔資源](logResource.md)

### [封裝資源](packageResource.md)

### [ProcessSet 資源](processSetResource.md)

### [登錄資源](registryResource.md)

### [指令碼資源](scriptResource.md)

### [服務資源](serviceResource.md)

### [ServiceSet 資源](serviceSetResource.md)

### [使用者資源](userResource.md)

### [WaitForAllResource](waitForAllResource.md)

### [WaitForAnyResource](waitForAnyResource.md)

### [WaitForSomeResource](waitForSomeResource.md)

### [WindowsFeature 資源](windowsfeatureResource.md)

### [WindowsFeatureSet 資源](windowsFeatureSetResource.md)

### [WindowsOptionalFeature 資源](windowsOptionalFeatureResource.md)

### [WindowsOptionalFeatureSet 資源](windowsOptionalFeatureSetResource.md)

### [WindowsPackageCab 資源](windowsPackageCabResource.md)

### [WindowsProcess 資源](windowsProcessResource.md)

## [撰寫自訂資源](authoringResource.md) 

### [使用 MOF 的自訂資源](authoringResourceMOF.md)

#### [C# 中使用 MOF 的資源](authoringResourceMofCS.md)

### [使用類別的自訂資源](authoringResourceClass.md)

### [複合資源](authoringResourceComposite.md)

### [撰寫單一執行個體的 DSC 資源 (最佳做法)](singleInstance.md)

### [資源撰寫檢查清單](resourceAuthoringChecklist.md)

## [對 DSC 資源執行偵錯](debugResource.md)

## [直接呼叫 DSC 資源方法](directCallResource.md)

# 本機設定管理員

## [設定本機設定管理員 (LCM)](metaConfig.md)

## [在 PowerShell 4.0 中設定 LCM](metaConfig4.md)

# DSC 提取模型

## [設定 Web 提取伺服器](pullServer.md)

## [設定 DSC SMB 提取伺服器](pullServerSMB.md)

## [設定提取用戶端](pullClient.md)

### [使用設定名稱設定提取用戶端](pullClientConfigNames.md)

### [使用設定識別碼設定提取用戶端](pullClientConfigID.md)

## [使用 DSC 報表伺服器](reportServer.md)

## [提取伺服器的最佳做法](secureServer.md)

# [DSC 範例](dscExamples.md)

## [使用 DSC、Pester 及 Visual Studio Team Services 來建置 CI/CD 管線](dscCiCd.md)

## [分離設定和環境資料](separatingEnvData.md)

# [疑難排解 DSC 的問題](troubleshooting.md)

# [在 Nano Server 上使用 DSC](nanoDsc.md)

# Linux 上的 DSC

## [開始使用 DSC for Linux](lnxGettingStarted.md)

## [適用於 Linux 的內建資源](lnxBuiltInResources.md)

### [nxArchive 資源](lnxArchiveResource.md)

### [nxEnvironment 資源](lnxEnvironmentResource.md)

### [nxFile 資源](lnxFileResource.md)

### [nxFileLine 資源](lnxFileLineResource.md)

### [nxGroup 資源](lnxGroupResource.md)

### [nxPackage 資源](lnxPackageResource.md)

### [nxService 資源](lnxServiceResource.md)

### [nxSshAuthorizedKeys 資源](lnxSshAuthorizedKeysResource.md)

### [nxUser 資源](lnxUserResource.md)

# [使用 Microsoft Azure 的 DSC](azureDsc.md)

# DSC MOF 參考

## [MSFT_DSCLocalConfigurationManager 類別](msft-dsclocalconfigurationmanager.md)

### [MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法](msft-dsclocalconfigurationmanager-applyconfiguration.md)

### [MSFT_DSCLocalConfigurationManager 類別的 DisableDebugConfiguration 方法](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)

### [MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)

### [MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法](msft-dsclocalconfigurationmanager-getconfiguration.md)

### [MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)

### [MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationStatus 方法](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)

### [MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)

### [MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)

### [MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法](msft-dsclocalconfigurationmanager-removeconfiguration.md)

### [MSFT_DSCLocalConfigurationManager 類別的 ResourceGet 方法](msft-dsclocalconfigurationmanager-resourceget.md)

### [MSFT_DSCLocalConfigurationManager 類別的 ResourceSet 方法](msft-dsclocalconfigurationmanager-resourceset.md)

### [MSFT_DSCLocalConfigurationManager 類別的 ResourceTest 方法](msft-dsclocalconfigurationmanager-resourcetest.md)

### [MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法](msft-dsclocalconfigurationmanager-rollback.md)

### [MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法](msft-dsclocalconfigurationmanager-sendconfiguration.md)

### [MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)

### [MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)

### [MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)

### [MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法](msft-dsclocalconfigurationmanager-stopconfiguration.md)

### [MSFT_DSCLocalConfigurationManager 類別的 TestConfiguration 方法](msft-dsclocalconfigurationmanager-testconfiguration.md)

# 其他資源

## [白皮書](whitepapers.md)
