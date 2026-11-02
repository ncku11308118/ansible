FROM mcr.microsoft.com/devcontainers/base:debian

COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

ENV UV_COMPILE_BYTECODE=1 \
	UV_LINK_MODE=copy \
	UV_PYTHON=3.14 \
	UV_PYTHON_INSTALL_DIR=/usr/local/share/uv/python \
	UV_TOOL_BIN_DIR=/usr/local/bin \
	UV_TOOL_DIR=/usr/local/share/uv/tools

RUN --mount=type=cache,target=/root/.cache/uv \
	uv tool install --with-executables-from ansible-core,ansible-lint ansible
RUN uv tool update-shell
