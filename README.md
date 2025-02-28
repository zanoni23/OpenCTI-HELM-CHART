# OpenCTI-HELM-CHART

This is a Helm chart for OpenCTI

## Pre requs

1. This chart is BYOEs (Bring your own Elastic)
2. Edit values

```yaml
# NGINX INGRESS OPTIONS
OPENCTI_INGRESS_HOST: ""
OPENCTI_TLS_SECRET: ""

HA_REPLICAS: 1
WORKER_REPLICAS: 3

# MINIO OPTIONS
MINIO_IMAGE: "minio/minio:RELEASE.2021-04-22T15-44-28Z"
MINIO_ACCESS_KEY: "" # UUID4
MINIO_SECRET_KEY: "" # UUID4

# RABBITMQ OPTIONS
RABBITMQ_IMAGE: "rabbitmq:3.8-management"
RABBITMQ_DEFAULT_PASS: ""
RABBITMQ_DEFAULT_USER: "OPENCTI"

# REDIS OPTIONS
REDIS_IMAGE: "redis:6.2.2"

# OPENCTI OPTIONS
OPENCTI_TOKEN: ""   # UUID4
LOG_LEVEL: "info"   # GLOBAL
ADMIN_EMAIL: ""
ADMIN_PASSWORD: ""

# ELASTICSEARCH OPTIONS
ELASTICSEARCH__URL: ""  # BYOES (Bring Your Own ES)
ELASTICSEARCH__SSL__REJECT_UNAUTHORIZED: "true"
ELASTICSEARCH__USERNAME: ""
ELASTICSEARCH__PASSWORD: ""

# SAML
SAML_ENABLED: false
PROVIDERS__SAML__STRATEGY: ""
PROVIDERS__SAML__CONFIG__ISSUER:  ""
PROVIDERS__SAML__CONFIG__ENTRY_POINT: ""
PROVIDERS__SAML__CONFIG__SAML_CALLBACK_URL: ""
PROVIDERS__SAML__CONFIG__CERT: ""

# CONNECTOR OPTIONS
CONFIDENCE_LEVEL: "15" # GLOBAL

# Other CONNECTOR OPTS
CONNECTOR_EXPORT_FILE_CSV_UUID: "0eb5fb53-6530-4fa9-b6bc-15b140938468"
CONNECTOR_EXPORT_FILE_STIX_UUID: "607868c8-e552-464a-99be-eff6143b60f2"
CONNECTOR_CONNECTOR_HISTORY_UUID: "dec90f8b-6e1e-4ae0-a654-6cadd989c7e9"
CONNECTOR_IMPORT_FILE_STIX_UUID: "73c2d142-d10c-47f9-b6ef-04f80a940c80"


# CONNECTOR CONNECTOR_IMPORT_REPORT
CONNECTOR_IMPORT_REPORT_UUID: "a4c89008-2166-407b-9091-d556fd1b6757"
IMPORT_REPORT_CREATE_INDICATOR: "false"
CONNECTOR_ONLY_CONTEXTUAL: "true"

# CONNECTOR OPENCTI
CONNECTOR_OPENCTI_ENABLED: false
CONNECTOR_OPENCTI_UUID: "891b04d2-6de2-45dd-9bc8-110ef396b1bc"
CONNECTOR_OPENCTI_CONNECTOR_UPDATE_EXISTING_DATA: "true"
CONNECTOR_OPENCTI_CONFIG_SECTORS_FILE_URL: "https://raw.githubusercontent.com/OpenCTI-Platform/datasets/master/data/sectors.json"
CONNECTOR_OPENCTI_CONFIG_GEOGRAPHY_FILE_URL: "https://raw.githubusercontent.com/OpenCTI-Platform/datasets/master/data/geography.json"
CONNECTOR_OPENCTI_INTERVAL: "7"


# CONNECTOR CVE
CONNECTOR_CVE_ENABLED: false
CONNECTOR_CVE_UUID: "891b04d2-6de2-45dd-9bc8-110ef396b1bc"
CONNECTOR_CVE_CONNECTOR_UPDATE_EXISTING_DATA: "true"
CONNECTOR_CVE_NVD_DATA_FEED: "https://nvd.nist.gov/feeds/json/cve/1.1/nvdcve-1.1-recent.json.gz"
CONNECTOR_CVE_HISTORY_DATA_FEED: "https://nvd.nist.gov/feeds/json/cve/1.1/"
CONNECTOR_CVE_INTERVAL: "1"

# CONNECTOR ALIENVAULT
CONNECTOR_ALIENVAULT_ENABLED: false
CONNECTOR_ALIENVAULT_UUID: "04867e1b-c5c0-4d78-9968-6a5543b30a9d"
CONNECTOR_ALIENVAULT_CONNECTOR_UPDATE_EXISTING_DATA: "true"
CONNECTOR_ALIENVAULT_BASE_URL: "https://otx.alienvault.com"
CONNECTOR_ALIENVAULT_API_KEY: "ChangeMe"
CONNECTOR_ALIENVAULT_TLP: "White"
CONNECTOR_ALIENVAULT_CREATE_OBSERVABLES: "true"
CONNECTOR_ALIENVAULT_CREATE_INDICATORS: "true"
CONNECTOR_ALIENVAULT_PULSE_START_TIMESTAMP: "2020-05-01T00:00:00"                  # BEWARE! Could be a lot of pulses!
CONNECTOR_ALIENVAULT_REPORT_TYPE: "threat-report"
CONNECTOR_ALIENVAULT_REPORT_STATUS: "New"
CONNECTOR_ALIENVAULT_GUESS_MALWARE: "false"                                        # Use tags to guess malware.
CONNECTOR_ALIENVAULT_GUESS_CVE: "false"                                            # Use tags to guess CVE.
CONNECTOR_ALIENVAULT_EXCLUDED_PULSE_INDICATOR_TYPES: "FileHash-MD5,FileHash-SHA1"  # Excluded Pulse indicator types.
CONNECTOR_ALIENVAULT_ENABLE_RELATIONSHIPS: "true"                                  # Enable/Disable relationship creation between SDOs.
CONNECTOR_ALIENVAULT_ENABLE_ATTACK_PATTERNS_INDICATES: "true"                      # Enable/Disable "indicates" relationships between indicators and attack patterns
CONNECTOR_ALIENVAULT_INTERVAL_SEC: "1800"

# CONNECTOR MITRE
CONNECTOR_MITRE_ENABLED: false
CONNECTOR_MITRE_UUID: "2ee50a39-3210-40a7-a4e7-c062fa20b636"
CONNECTOR_MITRE_CONNECTOR_UPDATE_EXISTING_DATA: "true"
CONNECTOR_MITRE_ENTERPRISE_FILE_URL: "https://raw.githubusercontent.com/mitre/cti/master/enterprise-attack/enterprise-attack.json"
CONNECTOR_MITRE_PRE_ATTACK_FILE_URL: "https://raw.githubusercontent.com/mitre/cti/master/pre-attack/pre-attack.json"
CONNECTOR_MITRE_MOBILE_ATTACK_FILE_URL: "https://raw.githubusercontent.com/mitre/cti/master/mobile-attack/mobile-attack.json"
CONNECTOR_MITRE_INTERVAL: "1" # In days, must be strictly greater than 1

# CONNECTOR Cuckoo
CONNECTOR_CUCKOO_ENABLED: false
CONNECTOR_CUCKOO_UUID: "f5f85c02-0439-11ec-95fe-00155ded4958"
CONNECTOR_CUCKOO_UPDATE_EXISTING_DATA: true
CONNECTOR_CUCKOO_CREATE_INDICATORS: true
CONNECTOR_CUCKOO_ENABLE_REGISTRY_KEYS: true
CONNECTOR_CUCKOO_ENABLE_NETWORK_TRAFFIC: true
CONNECTOR_CUCKOO_TLP: "AMBER"
CONNECTOR_CUCKOO_BASE_URL: "https://sandbox.no/"
CONNECTOR_CUCKOO_API_URL: "https://sandbox.no/api/"
CONNECTOR_CUCKOO_INTERVAL: 10
CONNECTOR_CUCKOO_REPORT_HISTORY_TIME: 1500
CONNECTOR_CUCKOO_VERIFY_SSL: false


# CONNECTOR URLHAUS
CONNECTOR_URLHAUS_ENABLED: false
CONNECTOR_URLHAUS_UUID: "a6cc0efb-ad28-4fbe-8f0a-7d47476b74ed"
CONNECTOR_URLHAUS_CSV_URL: "https://urlhaus.abuse.ch/downloads/csv_recent/"
CONNECTOR_URLHAUS_IMPORT_OFFLINE: "true"
CONNECTOR_URLHAUS_CREATE_INDICATORS: "true"
CONNECTOR_URLHAUS_INTERVAL: "1"
CONNECTOR_URLHAUS_UPDATE_EXISTING: "true"

# CONNECTOR VXVAULT
CONNECTOR_VXVAULT_ENABLED: false
CONNECTOR_VXVAULT_UUID: "718fabba-5b87-492e-ac3e-b38d282c2150"
CONNECTOR_VXVAULT_URL: "http://vxvault.net/URL_List.php"
CONNECTOR_VXVAULT_CREATE_INDICATORS: "true"
CONNECTOR_VXVAULT_INTERVAL: "1"
CONNECTOR_VXVAULT_UPDATE_EXISTING: "true"

# CONNECTOR MALPEDIA
CONNECTOR_MALPEDIA_ENABLED: false
CONNECTOR_MALPEDIA_UUID: "5099e8a1-451c-48d9-aab6-280bd0054f4e"
MALPEDIA_AUTH_KEY: ""
MALPEDIA_INTERVAL_SEC: "86400"
MALPEDIA_IMPORT_INTRUSION_SETS: "false"
MALPEDIA_IMPORT_YARA: "true"
MALPEDIA_CREATE_INDICATORS: "true"
MALPEDIA_CREATE_OBSERVABLES: "true"
CONNECTOR_MALPEDIA_UPDATE_EXISTING: "true"

# TAXII Connetors
CONNECTOR_TAXII_ENABLED: false
TAXII_SERVERS:
  - NAME: taxi1
    CONFIDENCE_LEVEL: "15"
    CONNECTOR_UUID: "83d7be21-1640-476b-98dd-a27ceb510f2c"
    UPDATE_EXISTING_DATA: "true"
    TAXII2_DISCOVERY_URL: ""
    TAXII2_USERNAME: ""
    TAXII2_PASSWORD: ""
    TAXII2_V21: "false"
    TAXII2_COLLECTIONS: "*.*"
    TAXII2_INITIAL_HISTORY: "24" # Hours
    TAXII2_INTERVAL: "100"
    VERIFY_SSL: "true"
  - NAME: taxi2
    CONFIDENCE_LEVEL: "15"
    CONNECTOR_UUID: "b7cda4dc-68f8-4172-8fc6-14752c65c607"
    UPDATE_EXISTING_DATA: "true"
    TAXII2_DISCOVERY_URL: ""
    TAXII2_USERNAME: ""
    TAXII2_PASSWORD: ""
    TAXII2_V21: "false"
    TAXII2_COLLECTIONS: "*.*"
    TAXII2_INITIAL_HISTORY: "24" # Hours
    TAXII2_INTERVAL: "100"
    VERIFY_SSL: "true"

# MISP Connetors
CONNECTOR_MISP_ENABLED: false
MISP_SERVERS:
  - NAME: MISP1
    CONFIDENCE_LEVEL: "15"
    CONNECTOR_UUID: "7fa5e4d2-41f9-479d-b26c-d77929ddd3b0"
    UPDATE_EXISTING_DATA: "true"
    MISP_URL: "http://localhost" # Required
    MISP_REFERENCE_URL: "" # Optional, will be used to create external reference to MISP event (default is "url")
    MISP_KEY: "ChangeMe" # Required
    MISP_SSL_VERIFY: "False" # Required
    MISP_DATETIME_ATTRIBUTE: "timestamp" # Required, filter to be used in query for new MISP events
    MISP_CREATE_REPORTS: "True" # Required, create report for MISP event
    MISP_CREATE_INDICATORS: "True" # Required, create indicators from attributes
    MISP_CREATE_OBSERVABLES: "True" # Required, create observables from attributes
    MISP_CREATE_OBJECT_OBSERVABLES: "True" # Required, create text observables for MISP objects
    MISP_REPORT_CLASS: "MISP Event" # Optional, report_class if creating report for event
    MISP_IMPORT_FROM_DATE: "2000-01-01" # Optional, import all event from this date
    MISP_IMPORT_TAGS: "opencti:import,type:osint" # Optional, list of tags used for import events
    MISP_IMPORT_TAGS_NOT: "" # Optional, list of tags to not include
    MISP_IMPORT_CREATOR_ORGS: "" # Optional, only import events created by this ORG (put the identifier here)
    MISP_IMPORT_OWNER_ORGS: "" # Optional, only import events owned by this ORG (put the identifier here)
    MISP_IMPORT_DISTRIBUTION_LEVELS: "0,1,2,3" # Optional, only import events with the given distribution levels
    MISP_IMPORT_THREAT_LEVELS: "1,2,3,4" # Optional only import events with the given threat levels
    MISP_IMPORT_ONLY_PUBLISHED: "False"
    MISP_IMPORT_WITH_ATTACHMENTS: "False" # Optional, try to import a PDF file from the attachment attribute
    MISP_IMPORT_TO_IDS_NO_SCORE: "40" # Optional, use as a score for the indicator/observable if the attribute to_ids is no
    MISP_INTERVAL: "1" # Required, in minutes
  - NAME: MISP2
    CONFIDENCE_LEVEL: "15"
    CONNECTOR_UUID: "9d1a0b9f-b361-41c6-8d46-10a8ef387165"
    UPDATE_EXISTING_DATA: "true"
    MISP_URL: "http://localhost" # Required
    MISP_REFERENCE_URL: "" # Optional, will be used to create external reference to MISP event (default is "url")
    MISP_KEY: "ChangeMe" # Required
    MISP_SSL_VERIFY: "False" # Required
    MISP_DATETIME_ATTRIBUTE: "timestamp" # Required, filter to be used in query for new MISP events
    MISP_CREATE_REPORTS: "True" # Required, create report for MISP event
    MISP_CREATE_INDICATORS: "True" # Required, create indicators from attributes
    MISP_CREATE_OBSERVABLES: "True" # Required, create observables from attributes
    MISP_CREATE_OBJECT_OBSERVABLES: "True" # Required, create text observables for MISP objects
    MISP_REPORT_CLASS: "MISP Event" # Optional, report_class if creating report for event
    MISP_IMPORT_FROM_DATE: "2000-01-01" # Optional, import all event from this date
    MISP_IMPORT_TAGS: "opencti:import,type:osint" # Optional, list of tags used for import events
    MISP_IMPORT_TAGS_NOT: "" # Optional, list of tags to not include
    MISP_IMPORT_CREATOR_ORGS: "" # Optional, only import events created by this ORG (put the identifier here)
    MISP_IMPORT_OWNER_ORGS: "" # Optional, only import events owned by this ORG (put the identifier here)
    MISP_IMPORT_DISTRIBUTION_LEVELS: "0,1,2,3" # Optional, only import events with the given distribution levels
    MISP_IMPORT_THREAT_LEVELS: "1,2,3,4" # Optional only import events with the given threat levels
    MISP_IMPORT_ONLY_PUBLISHED: "False"
    MISP_IMPORT_WITH_ATTACHMENTS: "False" # Optional, try to import a PDF file from the attachment attribute
    MISP_IMPORT_TO_IDS_NO_SCORE: "40" # Optional, use as a score for the indicator/observable if the attribute to_ids is no
    MISP_INTERVAL: "1" # Required, in minutes



# INTERNAL_ENRICHMENT

# CONNECTOR VT
CONNECTOR_VT_ENABLED: false
CONNECTOR_VT_UUID: "422c2fd8-55c3-4ef4-be7f-8e81103190ba"
CONNECTOR_VT_AUTO: "true"
CONNECTOR_VT_MAX_TLP: "TLP:AMBER"
CONNECTOR_VT_TOKEN: ""

# CONNECTOR ABUSEIPDB
CONNECTOR_ABUSEIPDB_ENABLED: false
CONNECTOR_ABUSEIPDB_UUID: "b0ee6f09-23d1-4c25-aea6-77198ae5b7b8"
CONNECTOR_ABUSEIPDB_AUTO: "true"
CONNECTOR_ABUSEIPDB_API_KEY: ""
CONNECTOR_ABUSEIPDB_MAX_TLP: "TLP:AMBER"

# CONNECTOR HYBRIDANALYSIS
CONNECTOR_HYBRID_ANALYSIS_ENABLED: false
CONNECTOR_HYBRID_ANALYSIS_UUID: "50176104-f368-4d32-a18f-ddd0098bb374"
CONNECTOR_HYBRID_ANALYSIS_AUTO: "true"
CONNECTOR_HYBRID_ANALYSIS_TOKEN: ""
CONNECTOR_HYBRID_ANALYSIS_ENVIRONMENT_ID: "110" # Available environments ID: 300: 'Linux (Ubuntu 16.04, 64 bit)', 200: 'Android Static Analysis', 120: 'Windows 7 64 bit', 110: 'Windows 7 32 bit (HWP Support)', 100: 'Windows 7 32 bit'
CONNECTOR_HYBRID_ANALYSIS_MAX_TLP: "TLP:AMBER"

# CONNECTOR IPINFO
CONNECTOR_IPINFO_ANALYSIS_ENABLED: false
CONNECTOR_IPINFO_UUID: "e57d4ee2-d5f3-40cd-b468-144fd91d1398"
CONNECTOR_IPINFO_AUTO: "true"
CONNECTOR_IPINFO_TOKEN: ""
CONNECTOR_IPINFO_MAX_TLP: "TLP:AMBER"

# CONNECTOR MALBEACON
CONNECTOR_MALBEACON_ANALYSIS_ENABLED: false
CONNECTOR_MALBEACON_UUID: "55e28f27-d57c-4dff-8adc-7a561a930de2"
CONNECTOR_MALBEACON_AUTO: "true"
CONNECTOR_MALBEACON_API_KEY: ""


# CONNECTOR SHODAN
CONNECTOR_SHODAN_ENABLED: false
CONNECTOR_SHODAN_UUID: "55e28f27-d57c-4dff-8adc-7a561a930de2"
CONNECTOR_SHODAN_AUTO: "true"
CONNECTOR_SHODAN_TOKEN: ""
CONNECTOR_SHODAN_MAX_TLP: "TLP:AMBER"
```