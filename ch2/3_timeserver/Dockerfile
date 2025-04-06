FROM python:3.12

# 强制 Python 将标准输出和标准错误流直接输出，不进行行缓冲或全缓冲
# 确保日志和打印语句实时显示在容器日志中，而不是等到缓冲区满或程序结束时才一次性输出
# 在容器化环境中特别有用，因为它使你能够立即看到应用程序的输出，便于调试和监控

# Force Python to use unbuffered output
# This ensures that logs and print statements are displayed in real-time
# instead of being buffered. This is particularly useful in containerized environments
# as it allows you to see the application output immediately, aiding in debugging and monitoring.
ENV PYTHONUNBUFFERED=1
COPY . /app
WORKDIR /app
CMD ["python3", "server.py"]