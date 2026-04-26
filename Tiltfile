print("""
-----------------------------------------------------------------
✨ SWE Microservices (Ingress-based Tilt setup)
-----------------------------------------------------------------
Access your app at: http://localhost
-----------------------------------------------------------------
""".strip())

docker_build("sinedon/ui", "../swe-ui")
docker_build("sinedon/edge-service", "../swe-edge-service")
docker_build("sinedon/content-access", "../swe-content-access")
docker_build("sinedon/content-manager", "../swe-content-manager")
docker_build("sinedon/progress-access", "../swe-progress-access")
docker_build("sinedon/progress-manager", "../swe-progress-manager")
docker_build("sinedon/completion-engine", "../swe-completion-engine")
docker_build("sinedon/event-processor", "../swe-event-processor")
docker_build("sinedon/config-service", "../swe-config-service")


k8s_yaml([
    "ui-deployment.yaml",
    "edge-service-deployment.yaml",
    "content-access-deployment.yaml",
    "content-manager-deployment.yaml",
    "progress-access-deployment.yaml",
    "progress-manager-deployment.yaml",
    "completion-engine-deployment.yaml",
    "event-processor-deployment.yaml",
    "mongo-deployment.yaml",
    "postgre-deployment.yaml",
    "rabbitmq-deployment.yaml",
    "ingress.yaml"
])

k8s_resource(
    "ui",
    links=["http://localhost"]
)
